# 01 — Architecture

## Architectural recommendation

Use a **local-first, 2D-first modular system**.

### Default technology choices

| Concern | Choice | Why |
|---|---|---|
| Authoring language | TypeScript | One language for scenes, tools and data contracts |
| 2D animation/editor | Motion Canvas | Built for code-driven vector animation; includes live editor/preview |
| Drawing | Motion Canvas 2D, SVG, Canvas | Lightweight baseline and precise graphic control |
| Encoding | FFmpeg | Mature, local media processing |
| Voice timing | Whisper-compatible transcription output | Reuse word/segment timestamps; transcription can be supplied externally |
| Metadata index | SQLite | Local, portable, no hosted service |
| Reference files | Normal folders + JSON metadata | Easy to inspect, back up and move |
| Research | Pluggable search/browser adapter | Avoid hard dependency on one search provider |
| Agent interface | Claude Code skills + CLAUDE.md | Reusable instructions and staged workflows |

Motion Canvas is the recommended first renderer because its project describes a TypeScript animation library plus a real-time editor, and its stated focus includes informative vector animation and voiceover synchronisation. Its FFmpeg exporter is documented as relatively new, so validate export reliability during the first technical spike.

### Optional specialist tools

Only add these after a concrete need is demonstrated:

- **Three.js:** genuine 3D scenes, spatial camera work, materials or particle systems. Keep it isolated in optional scenes.
- **GSAP:** advanced DOM/SVG timeline choreography where Motion Canvas primitives are insufficient. Avoid maintaining two competing animation timelines by default.
- **D3.js:** complex data transformations or specialised charts. Simple charts should use SVG directly.
- **Remotion:** consider if the project needs a React-centric video composition ecosystem, complex media timelines or a renderer that better fits the target workflow. Benchmark it against Motion Canvas before switching.
- **Playwright:** automated browser checks, reference page capture where permitted, and repeatable preview screenshots.
- **Whisper:** optional local transcription. Prefer a provided transcript with timestamps when available to avoid repeated transcription cost.

## High-level modules

1. **Creative Director**
   - Reads brief/script.
   - Asks the user for missing creative preferences.
   - Identifies story beats and audience.
   - Creates creative hypotheses.

2. **Reference Researcher**
   - Searches curated sources and the local vault.
   - Finds references by visual behaviour, not just topic.
   - Extracts source URL, creator, project, observed techniques and licensing notes.
   - Returns a compact evidence pack.

3. **Art Direction Compiler**
   - Converts approved direction into machine-usable design tokens and scene rules.
   - Defines type, palette, composition, materials, camera and motion language.
   - Creates a reference-to-rule mapping.

4. **Storyboard Planner**
   - Splits narration into scenes and beats.
   - Specifies visual purpose, composition, movement, timing and transitions.
   - Avoids writing implementation code at this stage.

5. **Scene Builder**
   - Selects the simplest suitable renderer/technique.
   - Builds reusable components and scenes.
   - Uses deterministic code for timings and layouts.

6. **Preview and Review**
   - Opens the live preview.
   - Captures key frames/contact sheets.
   - Collects timestamped and element-specific notes.

7. **Render Manager**
   - Renders only approved scenes or changed segments where supported.
   - Encodes via FFmpeg.
   - Keeps render settings conservative by default.

8. **Learning Curator**
   - Separates one-off preferences from recurring system defects.
   - Proposes changes to skills, rules or components.
   - Requires user approval before changing global creative rules.

## Architecture diagram

```text
USER BRIEF / SCRIPT
        |
        v
CREATIVE INTAKE <----> USER QUESTIONS
        |
        v
REFERENCE RESEARCH <----> LOCAL REFERENCE VAULT
        |
        v
CREATIVE DIRECTION + EVIDENCE
        |
        v
USER APPROVAL
        |
        v
ART DIRECTION TOKENS + STORYBOARD
        |
        v
SCENE BUILDER ----> REUSABLE COMPONENT LIBRARY
        |
        v
MOTION CANVAS PREVIEW
        |
        v
REVIEW NOTES <----> USER
        |
        v
TARGETED REVISIONS
        |
        v
FINAL RENDER + FFmpeg
        |
        v
POST-PROJECT LEARNING REVIEW
```

## Important boundaries

- The LLM decides what should be communicated and proposes visual choices.
- The reference system finds, stores and retrieves evidence.
- Code handles indexing, timestamps, rendering, file operations and validation.
- The renderer executes deterministic scene code.
- The user approves creative direction and final output.

Do not create an autonomous multi-agent architecture for the MVP. A single Claude Code session using focused skills and scripts is simpler, cheaper and easier to debug.
