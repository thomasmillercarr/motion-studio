# 05 — Low-resource hardware and token efficiency

## Can the system run on a low-end computer?

The authoring and preview workflow can be designed for modest hardware. Final render speed cannot be guaranteed without knowing the exact machine and scene complexity.

The largest avoidable cost is architectural overreach: multiple rendering frameworks, unnecessary 3D, large assets, repeated full renders and asking Claude to reason about work that deterministic scripts can handle.

## Hardware tiers

### Tier 1 — modest / integrated graphics
- 2D vector-first.
- Preview at 640×360 or 960×540.
- Preview at 12–24 fps where necessary.
- Keep scenes short during development.
- Avoid real-time 3D and heavy blur.
- Render sequentially.
- Export final 1080p only after approval; expect longer render times.

### Tier 2 — mainstream laptop / older dedicated GPU
- 2D-first with selective lightweight 3D.
- Preview at 960×540 or 1280×720.
- 24–30 fps preview depending on complexity.
- One render job at a time.
- Use modest texture sizes and restrained post-processing.

### Tier 3 — capable desktop / modern GPU
- More complex 3D and particles.
- Higher-resolution previews.
- Parallel rendering only after benchmarking memory and stability.

The application should detect hardware once and save a `hardware-profile.json`. Let the user override it.

## Low-resource defaults

- 2D scenes are the default.
- Avoid rendering at final resolution during creative iteration.
- Keep preview scale and preview frame rate independently configurable.
- Render only changed scenes or time ranges where the renderer supports it.
- Cache source assets, fonts, thumbnails and generated reference contact sheets.
- Reuse pre-rendered expensive effects where appropriate.
- Prefer SVG for crisp, simple vector graphics.
- Prefer Canvas for large numbers of simple repeated elements.
- Use WebGL/Three.js only when it materially improves the visual result.
- Avoid expensive real-time shadows, bloom, depth of field and multiple full-screen shader passes.
- Use static/baked lighting for 3D scenes when possible.
- Split long renders into chunks and resume safely.
- Limit default render concurrency to 1; benchmark before increasing.
- Store render settings per project.

## Token-efficiency principles

### Use Claude for high-value judgement
Claude should handle:
- Story interpretation.
- Creative direction.
- Reference synthesis.
- Visual technique selection.
- Scene composition decisions.
- Critique and revision proposals.

### Use code for deterministic work
Do not spend tokens asking Claude to:
- Count frames.
- Calculate timestamps.
- Rename files.
- Build contact sheets.
- Extract media metadata.
- Compare file hashes.
- Check missing assets.
- Validate JSON/YAML.
- Search exact tags.
- Run repetitive render commands.
- Reformat unchanged scene data.

### Context discipline
- Keep `CLAUDE.md` short and point to detailed skills.
- Load one or two relevant skills per task, not every skill.
- Return compact reference cards, not full page dumps.
- Summarise research once into `research-pack.md`.
- Store creative direction in project files so new sessions can resume without re-explaining.
- Start a fresh Claude Code session for a new project, reusing the approved system files.
- Ask for targeted diffs, not full rewrites of unrelated scenes.
- Keep a `project-state.md` with current stage, decisions, files changed and next action.
- Use structured outputs for scene plans and design tokens.
- Do not ask Claude to re-analyse references that have already been indexed unless the project question changes.

## Token budget policy

Every workflow stage should state:
- Expected LLM task.
- Files Claude needs to read.
- Deterministic scripts that can do the rest.
- Output file to write.
- Whether user approval is required.

Research should be capped initially at:
- 3 creative directions.
- 3–5 strong references per direction.
- 5–10 shortlisted references overall.
- One compact synthesis per direction.

Do not research endlessly. Stop when there is enough evidence to make a reasoned recommendation.

## Render policy

Use a draft profile during development and a final profile after approval.

Example configuration:

```json
{
  "preview": {
    "width": 960,
    "height": 540,
    "fps": 20,
    "scale": 0.5
  },
  "draft_render": {
    "width": 1280,
    "height": 720,
    "fps": 24,
    "concurrency": 1
  },
  "final_render": {
    "width": 1920,
    "height": 1080,
    "fps": 30,
    "concurrency": 1,
    "chunk_seconds": 10
  },
  "prefer_2d": true,
  "allow_3d": "only_when_justified"
}
```

These are starting defaults, not performance guarantees. Benchmark on the target computer and tune accordingly.
