# Claude Motion Studio — IDE Build Pack

A lean, reference-led motion graphics production system for Claude Code.

**Purpose:** make Claude a much stronger motion-design collaborator by giving it:
1. A repeatable creative-direction process.
2. A curated and searchable reference library.
3. Independent research capability with source tracking.
4. A lightweight, modular animation/rendering stack.
5. A feedback loop that improves the reusable system over time.

This is a **build specification**, not a prebuilt application. Open this folder in Claude Code, Cursor, VS Code or another coding IDE and start with `BUILD_PLAN.md` and `prompts/IDE_BUILD_PROMPT.md`.

## The key design decision

Do not make Claude invent visual taste from a blank prompt.

Before it designs a scene, it must:
- Understand the communication goal.
- Ask the user focused creative questions when important choices are unclear.
- Research suitable professional references independently.
- Search the local reference vault and component catalogue.
- Explain which visual principles it is borrowing and why.
- Propose a direction for approval before expensive implementation.

**Creative rule:** no visual technique should be used just because Claude knows how to implement it. Every technique must earn its place through the story, reference evidence and intended viewer response.

## Recommended lean stack

Start with **Motion Canvas + TypeScript + FFmpeg** for the first 2D-first production engine. Motion Canvas already provides a real-time editor/preview and is designed for vector animation and voiceover-synchronised explainers. Add other tools only when a real project requires them.

| Layer | Default | Add only when justified |
|---|---|---|
| Creative orchestration | Claude Code + Markdown skills | MCP/browser research adapter |
| 2D animation | Motion Canvas | GSAP for a specific timeline need |
| Vector graphics | SVG / Canvas | D3 for complex data visualisation |
| 3D | None in baseline | Three.js for scenes that genuinely need 3D |
| Audio/video | FFmpeg | Whisper-compatible transcription |
| Reference storage | Local files + SQLite | Hosted database only if collaboration requires it |
| Preview | Motion Canvas editor | Custom review UI only after MVP proves need |

Do not install Remotion, GSAP, Three.js, D3, multiple animation frameworks and a database on day one. Benchmark Motion Canvas first. Keep Remotion as a later alternative if the production requirements outgrow Motion Canvas.

## Hardware philosophy

The system should be comfortable to author on a modest computer:
- Use 2D vector scenes as the default.
- Preview at reduced resolution and frame rate.
- Render one job at a time by default.
- Avoid heavy blur, huge particle counts, high-resolution textures and unnecessary 3D.
- Use 3D selectively, with low-poly geometry, baked/static lighting and restrained post-processing.
- Cache generated assets, reference analysis and scene renders.
- Allow final rendering to be moved to a more powerful machine if needed.

A low-end machine can run the *workflow*, but render time depends on scene complexity, RAM, CPU, GPU, browser and output settings. No honest spec can guarantee real-time playback or fast 1080p/4K rendering on every low-end computer.

## Folder map

- `00_PRODUCT_BRIEF.md` — what we are building and what success means.
- `01_ARCHITECTURE.md` — system boundaries and technical decisions.
- `02_CREATIVE_DIRECTION.md` — user interview, independent research and direction approval.
- `03_REFERENCE_INTELLIGENCE.md` — reference research, ingestion, scoring and searchable vault.
- `04_VISUAL_LANGUAGE_CATALOGUE.md` — visual techniques and when to use them.
- `05_LOW_RESOURCE_AND_TOKEN_BUDGET.md` — hardware and token-saving rules.
- `06_PRODUCTION_WORKFLOW.md` — brief-to-export workflow.
- `07_SELF_IMPROVEMENT.md` — controlled learning from review feedback.
- `08_SKILLS_SPEC.md` — Claude Code skill responsibilities.
- `09_DATA_AND_FILE_CONTRACTS.md` — schemas and project conventions.
- `10_BUILD_PLAN.md` — sequential implementation plan.
- `11_ACCEPTANCE_TESTS.md` — objective MVP checks.
- `12_RESEARCH_SOURCES.md` — starting references and technical sources.
- `CLAUDE.md` — root instructions for the IDE agent.
- `prompts/` — copy-ready prompts for each stage.
- `skills/` — starter skill instructions to install in `.claude/skills/` during implementation.

## First milestone

A polished 15–20 second 16:9 motion-design sequence with:
- A clear approved creative direction.
- Three to five scenes.
- Strong typography and vector composition.
- At least one meaningful transition.
- One optional dimensional moment if the hardware supports it.
- Voiceover timing or a timed placeholder track.
- A live preview and a final MP4 export.
- A short review report with changes captured for future projects.

Do not start by building a large video editor. Prove the creative and rendering loop first.
