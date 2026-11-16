# 02 — Creative direction system

## Objective

Claude must not jump from script to animation. It must first form a defensible visual direction using user input and independent research.

The creative direction stage is a required gate before full scene production.

## Stage A: understand the communication problem

Extract:
- Subject and central argument.
- Target audience and assumed knowledge.
- What the viewer should understand, feel or remember.
- Tone and emotional progression.
- Runtime, aspect ratio and platform.
- Voiceover availability and timing.
- Required factual visuals, data, people, locations or historical material.
- Brand constraints and forbidden visual clichés.

## Stage B: ask the user, but do not interrogate them

Ask only questions whose answers could materially change the creative direction.

Good questions:
- “Which of these three visual directions feels closest: editorial typography, dimensional abstract graphics, or archival collage?”
- “Should this feel restrained and intellectual, energetic and experimental, or cinematic and dramatic?”
- “Do you have one or two examples of motion work you love? Links or screenshots are useful, but optional.”
- “Are there visual styles or clichés you definitely want to avoid?”

Rules:
- Ask at most 3–5 concise questions in one round.
- Offer a sensible default if the user does not know.
- Do not ask for preferences that can be inferred from the brief.
- Do not force the user to supply references; independent research is mandatory.
- If the user supplies references, treat them as high-priority evidence, not as instructions to copy.

## Stage C: independently research visual references

Research must search by *visual problem* as well as subject.

Example: for “the invisible network behind global shipping”, search for:
- abstract network animation,
- logistics data visualisation,
- editorial map motion design,
- typographic documentary title design,
- isometric infrastructure animation.

Use at least three different reference classes where relevant:
1. Professional motion design / studio work.
2. Editorial or documentary storytelling.
3. Technical examples, source projects or code demonstrations.

Do not treat a generic inspiration gallery as proof that an effect is technically reproducible.

## Stage D: analyse references

For each candidate, record:
- URL and project title.
- Creator/studio, if available.
- Source type and date accessed.
- What is visibly happening.
- Composition and hierarchy.
- Typography and treatment.
- Colour and materials.
- Motion behaviour and timing.
- Camera behaviour, if any.
- Transition design.
- Why it is relevant to this story.
- What principle can be adapted.
- What must not be copied.
- Confidence and any access limitations.

Distinguish observed facts from interpretation. If the page cannot be viewed, do not pretend to have analysed its animation. Record the limitation and use available stills, descriptions or other sources.

## Stage E: create three creative hypotheses

Claude should normally present three meaningfully different directions, not three colour palettes of the same idea.

Each direction includes:
- Name and one-sentence concept.
- Narrative rationale.
- Reference evidence (2–4 links where available).
- Composition system.
- Typography approach.
- Palette/material approach.
- Motion principles.
- Transition language.
- Example scene treatment.
- Complexity/performance estimate.
- Risks and likely clichés.

One direction may combine reference principles, but must explain the synthesis.

## Stage F: make a recommendation

Score each direction from 1–5 against:
- Story fit.
- Originality.
- Clarity.
- Visual sophistication.
- Feasibility on the target hardware.
- Consistency across the full runtime.
- Evidence quality.

Do not let a high score conceal weak evidence. Explain the trade-offs and recommend one direction.

## Stage G: user approval gate

Before production, show:
- Recommended direction.
- A compact moodboard/contact sheet.
- Design tokens.
- One representative frame or proof-of-style scene.
- A short motion test if movement is central to the concept.

Ask the user to approve, reject or adjust. Do not generate the entire film before this approval.

## Art direction output contract

Write `creative-direction.md` with:

```yaml
project:
  title: ""
  audience: ""
  runtime_seconds: 0
  aspect_ratio: "16:9"
  emotional_arc: []

direction:
  name: ""
  thesis: ""
  story_fit: ""
  originality_note: ""

references:
  - id: "REF-001"
    url: ""
    creator: ""
    observed_principle: ""
    adaptation: ""
    do_not_copy: ""

visual_system:
  palette: []
  typography: []
  composition_rules: []
  materials: []
  camera_rules: []
  motion_rules: []
  transition_rules: []
  texture_rules: []

constraints:
  avoid: []
  hardware_profile: "low-resource"
  preferred_render_mode: "2d-first"

approval:
  status: "pending"
  user_notes: []
```

The YAML is a data contract; the full document should also contain readable explanations and visual examples.
