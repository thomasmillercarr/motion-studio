# 06 — Production workflow

## Stage 0 — Project intake

Input: brief, script, optional voiceover, optional references.

Outputs:
- `brief.md`
- `script.md`
- `project-state.md`

Do not ask the user to repeat information already present in files.

## Stage 1 — Creative intake

Claude extracts audience, message, tone, runtime, platform and constraints. It asks only high-impact missing questions.

Output: `creative-intake.md`

## Stage 2 — Research

Search local references first, then research externally if needed. Build compact reference cards and a comparison.

Outputs:
- `research-pack.md`
- `references/selected-references.json`
- permitted local thumbnails/contact sheet

## Stage 3 — Creative direction

Propose three distinct directions, score them, recommend one and explain trade-offs.

Output: `creative-direction.md`

Gate: user approval.

## Stage 4 — Storyboard and animatic

Split the script into scenes. Each scene must state:
- Narration or message.
- Duration and time range.
- Visual purpose.
- Main composition.
- Focal point.
- Elements entering, changing and leaving.
- Motion principle and easing.
- Transition to next scene.
- Selected reference principle.
- Technical implementation.
- Performance tier.

Outputs:
- `storyboard.md`
- `storyboard.json`
- A rough animatic / static frame sequence.

Gate: approve overall structure before detailed animation.

## Stage 5 — Proof of style

Build one representative scene or 3–5 second motion test.

Check:
- Does it feel like the approved direction?
- Is the motion intentional?
- Does it communicate the idea?
- Is the reference principle adapted rather than copied?
- Does it perform on the target hardware?

Gate: user approval.

## Stage 6 — Production

Build scenes using reusable components. Keep each scene independently previewable. Use shared tokens for type, palette, spacing, materials and motion.

Output: scene source files and a component inventory.

## Stage 7 — Audio and timing

If a voiceover exists:
- Use existing transcript/timestamps where available.
- Otherwise transcribe once using the configured tool.
- Store the transcript and timing data.
- Align scene boundaries to meaningful speech beats.
- Leave pauses where the visual idea needs room.
- Avoid forcing every word to trigger a new animation.

Outputs:
- `transcript.json`
- `audio-cue-sheet.md`

## Stage 8 — Review

Generate representative stills/contact sheets at:
- Scene opening.
- Key action.
- Scene ending.
- Transition boundaries.

User feedback should support:
- Timestamp notes.
- Scene-level notes.
- Element-level notes where feasible.

Claude should translate feedback into a small targeted change list.

Output: `review-round-XX.md`

## Stage 9 — Final render

- Validate assets and fonts.
- Run a short render test.
- Render changed scenes/ranges where supported.
- Use conservative concurrency.
- Encode via FFmpeg.
- Verify duration, dimensions, frame rate and audio presence.

Outputs:
- Final MP4.
- Render log.
- `delivery-report.md`

## Stage 10 — Learning review

Classify feedback:
- Project-specific preference.
- Reusable design principle.
- Repeated Claude failure.
- Engine bug.
- Hardware/performance issue.

Propose updates to skills, reference tags, components or automated tests. Require approval for changes to global rules.
