# 07 — Self-improvement and memory

## Goal

The system should improve from production experience without turning every subjective comment into a permanent rule.

## Four learning layers

### 1. Project memory
Stores decisions specific to one film:
- Approved direction.
- User comments.
- Scene changes.
- Asset choices.
- Render settings.

Location: `projects/<project>/project-state.md` and `feedback/`.

### 2. Reference memory
Stores reusable visual knowledge:
- What a reference demonstrates.
- Tags and technique descriptions.
- Adaptation notes.
- Provenance and creator attribution.

Location: `reference-vault/`.

### 3. Component memory
Stores working reusable implementations:
- Components.
- Parameters.
- Example use.
- Performance notes.
- Known limitations.
- Licence/provenance.

Location: `library/`.

### 4. Skill memory
Stores general rules that should affect future work:
- Common composition errors.
- Typography defects.
- Timing problems.
- Continuity rules.
- Rendering pitfalls.
- Better creative decision heuristics.

Location: `.claude/skills/` and `quality-rules/`.

## Feedback classification

Every review note must be assigned one of:

| Type | Example | Where it belongs |
|---|---|---|
| Project-specific | “Make this title warmer” | Project state |
| User preference | “I prefer restrained typography” | User preference profile, with confirmation |
| Reusable design principle | “Keep labels outside the focal image” | Relevant skill |
| Repeated agent failure | “Claude keeps using random camera orbits” | Skill + regression example |
| Engine defect | “SVG mask clips at frame boundary” | Code fix + automated test |
| Performance issue | “Preview drops frames with 5000 particles” | Performance rules |

## Learning loop

1. Capture raw feedback.
2. Classify it.
3. Check whether the issue has occurred before.
4. Identify root cause.
5. Propose the smallest reusable correction.
6. Add a before/after example or test.
7. Ask the user to approve global skill changes.
8. Update the skill and changelog.
9. Re-test a representative previous scene.

## Do not learn these things automatically

- A one-off aesthetic preference as a universal rule.
- A correction that applies only to one scene.
- A subjective comment without enough context.
- A workaround that creates a worse general result.
- A reference-specific layout or distinctive asset as a reusable template.

## Regression library

For every recurring defect, keep:
- Short description.
- Example frame or project path.
- Root cause.
- Corrective rule.
- Test procedure.
- Date added.

Examples:
- Text clipped by mask at scene boundary.
- Labels overlap the hero object.
- Camera movement has no narrative motivation.
- Particle density overwhelms typography.
- Scene transition changes the established grid.
- 3D objects drift or intersect unexpectedly.

## Change control

Claude may draft proposed changes, but must not silently rewrite core creative rules. Use:
- `learning/proposals/`
- `learning/approved/`
- `learning/rejected/`
- `learning/changelog.md`

This creates a system that improves deliberately rather than accumulating contradictory instructions.
