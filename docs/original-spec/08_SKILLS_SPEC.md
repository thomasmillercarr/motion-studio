# 08 — Claude Code skills specification

Install these as project-level skills under `.claude/skills/`. Keep each skill focused and load it only when relevant.

## Required skills

### motion-director
Purpose: interpret the brief and decide what the viewer should see and feel.
Must:
- Identify narrative beats.
- Ask concise creative questions.
- Search reference vault and external sources.
- Compare visual approaches.
- Apply the technique-selection test.
- Produce a recommendation and approval gate.
Must not: start coding full scenes before direction approval.

### reference-researcher
Purpose: find, analyse and catalogue high-quality references.
Must:
- Search local vault first.
- Search curated source list.
- Track provenance and access status.
- Distinguish observation from interpretation.
- Extract adaptable principles.
- Return concise evidence cards.
Must not: claim to have watched inaccessible content or copy protected work.

### art-director
Purpose: turn the approved direction into a consistent visual system.
Must define:
- Typography hierarchy.
- Palette.
- Grid and composition rules.
- Shapes and materials.
- Motion principles.
- Camera rules.
- Transition rules.
- Anti-patterns.
Output: `design-system.md` and machine-readable tokens.

### storyboard-planner
Purpose: create scene-level visual plans before implementation.
Must define timing, focal point, visual purpose, movement, transition and reference mapping for each scene.

### motion-implementer
Purpose: implement approved scenes using the simplest suitable engine.
Must:
- Prefer existing components.
- Keep scenes deterministic.
- Reuse design tokens.
- Make each scene independently testable.
- Avoid adding dependencies without approval.

### audio-sync
Purpose: align narration, scene boundaries and motion.
Must reuse existing transcript timing; do not repeatedly transcribe or infer precise word timing from plain text.

### visual-reviewer
Purpose: inspect contact sheets, preview frames and user feedback.
Must critique hierarchy, readability, motion, consistency, pacing, continuity and technical defects.
Must provide specific, actionable changes rather than generic praise.

### render-manager
Purpose: run draft/final exports efficiently.
Must:
- Check hardware profile.
- Use low-resource defaults.
- Render sequentially unless benchmarked otherwise.
- Chunk long renders where supported.
- Verify output metadata and audio.

### learning-curator
Purpose: classify review notes and propose reusable improvements.
Must distinguish project preference from global rule and require approval for global changes.

## Skill design rule

Each skill should contain:
- When to use it.
- Inputs it expects.
- Step-by-step workflow.
- Output files.
- Constraints.
- Failure modes.
- A short quality checklist.

Avoid duplicating the same long instructions across every skill. Put global principles in `CLAUDE.md` and link to the relevant skill.
