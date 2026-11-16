# CLAUDE.md

motion-studio is a Claude Code plugin of four skills: `studio` → `reference-research` →
`beatfilm` → `film-review`. See README.md. The skills are the product. Edit `SKILL.md` files and
their `references/` with care, and keep them short. They load into every film's context.

## Non-negotiable creative principle

No visual technique is used because it can be implemented. Every technique serves the story and
has a stated reason, ideally a reference principle. No stick figures, generic explainer tropes,
floating icons or stock dashboards. Never claim to have viewed a reference that could not be accessed.

## Rules

- `films/` is private client and personal work: gitignored, never committed or pushed, never `git add -f`.
- `taste/verdicts.md` and the skills change only with the user's approval. Do not promote one-off feedback into rules.
- beatfilm has no npm dependencies and no package.json, by design. Node ≥ 22 stdlib only.
- Each film dir holds its own copy of `bf.js`. After changing `skills/beatfilm/runtime/bf.js`, copy
  it into `skills/beatfilm/examples/kairo/bf.js`.
- Reference cards hold links and our own words only, never copied media.
- Credit Apache-2.0 sources in NOTICE when adapting their principles.

## Checks

```bash
node skills/beatfilm/scripts/render.mjs check skills/beatfilm/examples/kairo
node skills/beatfilm/scripts/render.mjs render skills/beatfilm/examples/kairo --res 720
```

For `beats.mjs` changes, check timing against a synthetic click track (clicks every 0.5 s) and confirm `--info` beats land within a few ms.

## Architecture

Three layers, joined by files in a film dir (`films/<slug>/` or `examples/kairo/`):

1. **`skills/beatfilm/scripts/beats.mjs`** decodes with ffmpeg to 22.05 kHz mono and computes spectral-flux onsets
   (full band and a <150 Hz kick band). Tempo comes from autocorrelation with a 120 bpm prior and an octave
   check. Beats come from Ellis DP, refit to a steady grid when residuals are under 25 ms. It then estimates the
   downbeat phase heuristically, and per-beat energy and hits (accents relative to neighbouring beats). Finally
   it picks a phrase-aligned window of N bars plus a faded tail, writes `audio/cut.m4a`, and writes `beats.json`
   with all times rebased so **t=0 = the cut's first downbeat**. The film timeline and the audio timeline are
   therefore identical. `LAG = 0.035` corrects flux peaking before the audible onset (measured); don't remove it.
2. **`skills/beatfilm/runtime/bf.js`** is the in-page runtime (global `BF`): easing, keyframes, seeded rng/noise, beat helpers,
   `set()`, `split()`, `mblur()`, `grain()`, and `BF.film({...setup(B)})`. `BF.film` sets the `window.film` contract
   (`width, height, fps, frames, audio, ready, render(t, f)`) that the renderer drives. Outside render mode
   (`window.__BF_RENDER` unset) the same page runs a live player synced to the audio. **Each film dir holds its
   own copy of `bf.js`** (from `init`): after changing `skills/beatfilm/runtime/bf.js`, copy it into every film/example.
3. **`skills/beatfilm/scripts/render.mjs`** runs a stdlib HTTP server over the film dir and drives N headless Chrome processes
   over raw CDP (its own tiny client). Each worker renders a contiguous frame chunk at
   `deviceScaleFactor = target / page size` (true 4K raster) and pipes JPEGs into its own x264. Chunks are
   concat-copied and the cut audio is muxed in. The frame count is verified with ffprobe.

## Invariants and gotchas (each one was a real bug)

- A film frame must be a **pure function of `t`**: workers render out of order. `check` re-renders probe frames
  after others and fails below 45 dB PSNR. Tiny diffs (GPU blur raster) only warn.
- `BF.set(el, {o})` writes `visibility: ''`, never `'visible'`. An explicit `visible` child overrides a hidden
  parent scene and leaks it into other scenes.
- In render mode `BF.grain()` only records `{amount, size}`; the renderer adds the grain in ffmpeg (luma noise
  + overlay blend). An in-page 4K grain overlay tripled render time. Stills don't show grain.
- Encoding (x264 `faster`, CRF 18, VBV cap ~45 Mbps at 4K, scaled by pixel count) is the 4K bottleneck, not Chrome.
- Chrome JPEG screenshots are BT.601 full range; the encode converts to BT.709 tv explicitly.
- `bundle` order matters: local `<script src>` tags are swapped for placeholders **first** and restored last.
  If the runtime is inlined early, its comments match the `beats:`/`audio:` regexes; if `src=` is rewritten
  first, scripts become `data:` URLs, which the Artifact CSP blocks. `<meta charset>` is kept.
- On Windows, Chrome holds `DevToolsActivePort` locked while writing it (EBUSY); the launch poll tolerates that.
- ffmpeg `drawtext` on Windows needs an explicit `fontfile` with the drive colon escaped (`C\\:/…`).
- Music is real recordings only (incompetech, CC BY 4.0, or the user's track); never synthesise music or SFX.
  `CREDITS.txt` must ship with any film, and `bundle` shows it in the player bar.
