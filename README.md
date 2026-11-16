# motion-studio

Claude skills for making motion-design films that don't look generated. You give a brief.
Claude asks the few questions that matter, researches real references, proposes three different
directions with the evidence behind each, and waits for your pick. Then it builds the film in
code, cuts it to the beat of real music and renders an MP4.

```
/motion-studio:studio  Kairo is a calendar that plans your week for you. Launch film for the website, 30 s.
```

| Skill | Job |
| --- | --- |
| `studio` | Intake, research, three directions, approval, handoff. Start here. |
| `reference-research` | Reference cards with sources, observed facts kept apart from interpretation, stored in `vault/`. |
| `beatfilm` | Builds the approved film as one HTML page drawn from time, cuts it to a measured beat map and renders 4K with headless Chrome + ffmpeg. |
| `film-review` | Checks the render honestly before it is called done; logs your feedback without turning one comment into a rule. |

The rule behind all four: **no technique is used just because it can be built.** Every
transition, type move and effect has to trace back to the story, a reference principle or a
stated reason.

## Install

**Claude Code** (full pipeline, renders MP4):

```bash
claude plugin marketplace add thomasmillercarr/motion-studio
claude plugin install motion-studio@motion-studio
```

Then `/motion-studio:studio <brief>`, or `/motion-studio:beatfilm <brief>` to skip the direction stage.
(Plain requests like "make me a launch film for…" also start with studio.)
Needs Node ≥ 22, ffmpeg on PATH and Chrome or Edge. No npm installs.

**Claude chat** (claude.ai, desktop, mobile): download the skill zips from the
[latest release](https://github.com/thomasmillercarr/motion-studio/releases/latest) and upload each
one in Settings → Capabilities → Skills. In chat you get the research, the directions and a live,
silent draft of the film as an Artifact. The MP4 is rendered in Claude Code or by GitHub Actions.

**Working locally:** clone this repo and run `claude --plugin-dir .` inside it, so the skills load
from your working copy. `vault/` and `taste/` are here too. Films go in `films/`, which is gitignored.

## Render anywhere

`.github/workflows/render.yml` renders a film directory on a GitHub-hosted Linux runner. Start it
from the Actions tab or the GitHub mobile app, and the MP4 (with the music credit) arrives as a job
artifact. It refuses any film whose `direction.md` is not approved.

Client films should never sit in this public repo. For automated or scheduled renders, keep
films in a **private** repo with the same workflow file and a `schedule:` trigger. The workflow
needs this repo's `skills/beatfilm/scripts` and `runtime`, which it can get by checking out
`thomasmillercarr/motion-studio` as a second step. The creative stages can run unattended too,
but they stop at the approval gate: nothing is rendered until you approve a direction.

## How beatfilm works

| Piece | What it does |
| --- | --- |
| `scripts/music.mjs` | searches Kevin MacLeod's incompetech catalogue (~1,400 CC BY tracks) by feel and bpm, and fetches a track with its credit line |
| `scripts/beats.mjs` | finds onsets, tempo, beats, downbeats, energy and hits, then cuts a phrase-aligned window of whole bars plus a faded tail |
| `runtime/bf.js` | the in-page runtime: easing, keyframes, seeded noise, beat helpers, text splitting, motion blur, grain, a live player, and `BF.grid()` for drafts with no track |
| `scripts/render.mjs` | `check` (contract, fonts, network, determinism), `stills` (contact sheet), `render` (parallel headless Chrome → x264 → MP4), `bundle` (one self-contained preview file for an Artifact) |
| `examples/kairo/` | a complete 30 s reference film |

## Credits

The transition rules, the never-ship list and the idea worksheet are adapted from
[HyperFrames](https://github.com/heygen-com/hyperframes) and
[motionmaxxing](https://github.com/Tejashmakwana/motionmaxxing). Those three files stay under
Apache-2.0; see `NOTICE`. beatfilm's pipeline is our own, informed by public descriptions of AI
motion-graphics workflows. It contains no Higgsfield code, prompts or documents and is not
affiliated with or endorsed by Higgsfield. Example music is CC BY 4.0 Kevin MacLeod.

`docs/original-spec/` is the build pack this started from, kept for reference. The skills replace its 10-phase plan.

MIT licence, except the three Apache-2.0 files listed in `NOTICE`.
