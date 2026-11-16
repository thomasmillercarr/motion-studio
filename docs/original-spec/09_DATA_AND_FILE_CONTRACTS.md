# 09 — Data and file contracts

## Project folder convention

```text
projects/
  project-slug/
    brief.md
    script.md
    project-state.md
    creative-intake.md
    research-pack.md
    creative-direction.md
    design-system.md
    storyboard.md
    storyboard.json
    audio/
    transcript/
    references/
    assets/
    scenes/
    review/
    renders/
    exports/
    delivery-report.md
```

## Reference vault convention

```text
reference-vault/
  sources/
    reference-sources.json
  records/
    REF-0001.json
  thumbnails/
  user-supplied/
  contact-sheets/
  index/
    references.sqlite
```

## Scene JSON contract

```json
{
  "scene_id": "SC-001",
  "title": "Opening statement",
  "start_frame": 0,
  "duration_frames": 120,
  "narration": "Opening line...",
  "purpose": "Establish the central tension.",
  "focal_point": "The oversized headline.",
  "composition": "Headline occupies left two-thirds; small data motif anchors lower right.",
  "reference_ids": ["REF-0001"],
  "adapted_principles": ["Masked reveal with deliberate negative space."],
  "techniques": ["kinetic_typography", "svg_mask"],
  "motion": {
    "entry": "mask_reveal",
    "easing": "custom_ease",
    "exit": "shape_transform"
  },
  "transition_to_next": "line_continuity",
  "engine": "motion_canvas_2d",
  "performance_tier": "low",
  "approval_status": "pending"
}
```

## SQLite tables

Minimum viable tables:
- `references`
- `reference_tags`
- `reference_techniques`
- `sources`
- `projects`
- `project_references`

Use SQLite FTS5 for searchable title, description, tags and notes. Start without embeddings/vector search.

## Configuration files

- `config/hardware-profile.json`
- `config/render-profiles.json`
- `config/research-providers.json`
- `data/reference-sources.json`

Do not store API keys in tracked JSON or Markdown. Use environment variables and a local `.env` excluded from version control when a provider requires credentials.

## Provenance and licensing

Every stored asset or code sample must record:
- Origin URL or local owner.
- Creator, if known.
- Licence or permission status.
- Allowed use.
- Attribution requirements.
- Whether it is reference-only or production-ready.

Do not place unlicensed reference media into final exports. Use original recreations, user-owned assets or properly licensed material.
