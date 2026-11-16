# 11 — Acceptance tests

## Creative direction

- Given a script, Claude identifies audience, message and emotional arc.
- Claude asks only high-impact missing questions.
- Claude searches the local vault before external research.
- Claude returns at least two genuinely distinct visual directions; target three.
- Each direction cites specific references and extracted principles.
- Claude explains why the selected techniques serve the story.
- Claude does not default to stick figures or generic explainer tropes.
- No full production begins before direction approval.

## Reference intelligence

- A user can add a URL and a local image.
- The system records provenance and access status.
- Search returns relevant references by tag and text.
- Search results include source links.
- Inaccessible pages are clearly marked.
- Reference analysis distinguishes observation from interpretation.
- The system does not scrape restricted pages or copy protected assets.

## Hardware and performance

- Hardware profile is recorded.
- Preview resolution and frame rate can be lowered independently of final export.
- Default render concurrency is one.
- A short render completes on the target machine.
- Render logs record time, resolution, fps and failure state.
- The system can resume or rerender changed chunks where supported.
- Optional 3D is disabled unless explicitly justified.

## Production

- A storyboard can be generated from a script.
- Scene timing is frame-based and deterministic.
- Every scene references its purpose and selected design principles.
- A representative scene can be previewed before full production.
- FFmpeg export produces a valid MP4.
- Output dimensions, frame rate, duration and audio are verified.

## Self-improvement

- Feedback is captured with project and scene context.
- Feedback is classified correctly.
- One-off preferences are not silently promoted to global rules.
- Repeated defects produce a proposed skill or regression-test update.
- Global rules require user approval.

## MVP demonstration

Produce a 15–20 second film with:
- 3–5 scenes.
- One approved creative direction.
- At least three documented reference principles.
- Kinetic typography.
- Layered vector composition.
- One intentional transition.
- Narration or timed voiceover placeholder.
- Preview and final MP4.
- A post-project learning report.
