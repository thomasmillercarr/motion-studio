# 10 — Sequential build plan

Build in small stages. Do not let Claude scaffold the entire system before validating the foundation.

## Phase 0 — Environment audit

Tasks:
- Inspect OS, CPU, RAM, GPU, Node and FFmpeg availability.
- Check disk space and current IDE environment.
- Confirm whether browser research or search tools are available.
- Record a hardware profile.
- Do not install optional libraries yet.

Deliverables:
- `ENVIRONMENT_REPORT.md`
- `config/hardware-profile.json`

Acceptance:
- The agent can explain what the machine can reasonably preview and render.
- No unnecessary dependencies installed.

## Phase 1 — Minimal Motion Canvas proof

Tasks:
- Scaffold a TypeScript Motion Canvas project.
- Run its editor and live preview.
- Create a 5-second typography/vector test.
- Export an image sequence and an MP4 using the selected exporter/FFmpeg.
- Measure preview responsiveness and render time.

Deliverables:
- Working preview.
- 5-second MP4.
- `ENGINE_SPIKE_REPORT.md`.

Decision gate:
- Continue with Motion Canvas if preview, export and authoring are reliable.
- Benchmark Remotion only if Motion Canvas fails a concrete requirement.
- Do not keep two engines by default.

## Phase 2 — Reference vault MVP

Tasks:
- Create reference source catalogue.
- Implement manual URL and local-image ingestion.
- Add structured reference records.
- Create SQLite index with FTS5 and tags.
- Add a CLI command to search and list references.
- Add contact-sheet generation for permitted local images.

Deliverables:
- Searchable local vault.
- At least 10 manually curated references.
- Reference ingestion and retrieval tests.

## Phase 3 — Research adapter

Tasks:
- Inspect available search/browser capabilities.
- Implement one adapter only.
- Search by visual problem and technique.
- Store URLs and compact metadata.
- Handle blocked/inaccessible pages honestly.
- Add deduplication and source provenance.

Deliverables:
- `research` command or script.
- `research-pack.md` output.

Do not add multiple paid search APIs in the MVP.

## Phase 4 — Creative direction workflow

Tasks:
- Implement intake questions.
- Create three creative directions.
- Add scoring and recommendation.
- Map reference principles to design rules.
- Add user approval gate.

Deliverables:
- Example creative-direction.md.
- Direction generation checklist.
- Approval state.

## Phase 5 — Design tokens and storyboard

Tasks:
- Convert approved direction into design tokens.
- Define scene JSON schema.
- Build storyboard output and rough animatic.
- Validate timings and missing reference IDs.

Deliverables:
- `design-system.md`
- `design-tokens.json`
- `storyboard.json`
- contact sheet / animatic.

## Phase 6 — Scene/component library

Start with:
- Typography reveal.
- Kinetic headline.
- SVG mask transition.
- Geometric line system.
- Data counter/chart.
- Editorial image crop/pan.
- Layered parallax composition.

Each component needs:
- Parameters.
- Example.
- Performance notes.
- Screenshot or rendered sample.
- Tests where feasible.

## Phase 7 — Preview and review loop

Tasks:
- Use the Motion Canvas editor as the initial preview.
- Generate keyframe/contact sheets.
- Store timestamped feedback.
- Convert notes into targeted scene changes.
- Avoid building a custom review application unless necessary.

## Phase 8 — Audio and final render

Tasks:
- Accept supplied transcript/timestamps.
- Add optional transcription adapter.
- Align scene durations.
- Add FFmpeg finalisation.
- Render chunks and verify output.

## Phase 9 — Learning system

Tasks:
- Classify feedback.
- Detect repeated issues.
- Propose skill/component changes.
- Add regression examples.
- Require approval for global rule changes.

## Phase 10 — Optional capabilities

Only add when a real production needs them:
- Three.js scenes.
- GSAP.
- D3.
- Remotion adapter.
- More research providers.
- Vector embeddings.
- Custom review UI.
- Remote rendering.

## Build discipline

At each phase:
1. Read only the relevant spec and skill.
2. State the intended files and commands.
3. Implement the smallest working slice.
4. Run tests and show output.
5. Update `project-state.md`.
6. Stop at the phase gate for review.

Do not proceed through every phase in one unreviewed agent run.
