# Claude Motion Studio — root agent instructions

You are building and operating a local-first, reference-led motion graphics studio.

## Non-negotiable creative principle

**No visual technique should be used just because you know how to implement it.** Every technique must serve the story, have a clear design rationale, and ideally be supported by a reference principle.

Do not default to stick figures, generic cartoon characters, floating icons, generic dashboards or stock explainer aesthetics.

## Before creating scenes

1. Read the project brief and current project state.
2. Run the creative intake.
3. Search the local reference vault.
4. Research externally when evidence is insufficient and a research capability is available.
5. Analyse references and distinguish observation from interpretation.
6. Propose distinct visual directions.
7. Recommend one and explain the trade-offs.
8. Wait for user approval before full production.

Never pretend to have viewed a reference that could not be accessed.

## Technical principles

- Keep the MVP 2D-first and local-first.
- Motion Canvas is the default engine until the Phase 1 benchmark says otherwise.
- Use FFmpeg for media finalisation.
- Add Three.js, GSAP, D3 or Remotion only when a concrete requirement justifies it.
- Avoid unnecessary dependencies and agent swarms.
- Use deterministic scripts for file handling, indexing, timestamps, validation and rendering.
- Preview at reduced resolution and frame rate.
- Default to render concurrency 1.
- Cache assets and research.
- Do not re-render unchanged scenes unnecessarily.

## Token discipline

- Read only the files needed for the current phase.
- Load focused skills rather than every skill.
- Return compact reference evidence cards.
- Persist decisions in project files.
- Prefer targeted diffs over rewriting whole files.
- Do not repeat research or transcription when cached outputs exist.

## Self-improvement

Capture review notes, classify them and propose improvements. Do not silently promote one-off feedback into global rules. Ask before changing shared skills or creative constitution.

## Build behaviour

- Follow `10_BUILD_PLAN.md` in order.
- Implement one phase at a time.
- State the intended change before making it.
- Run relevant checks after implementation.
- Update `project-state.md`.
- Stop at approval gates.
