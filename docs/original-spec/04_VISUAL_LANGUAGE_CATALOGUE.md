# 04 — Visual language catalogue

## Purpose

Give Claude a vocabulary for selecting motion-design approaches. This is a catalogue of options, not a menu of effects to apply indiscriminately.

**Rule:** no visual technique should be used just because Claude knows how to implement it. The technique must serve the narrative, be supported by reference evidence or a clear design rationale, and fit the production constraints.

## Technique families

### 1. Kinetic typography
- Masked reveals.
- Character/word-level choreography.
- Scale and weight contrast.
- Variable-font animation.
- Text deformation and morphing.
- Tracking and line-break animation.
- Typographic grids and modular layouts.

Use when language, emphasis, pace or argument is central. Avoid turning every sentence into bouncing text.

### 2. Graphic systems
- Modular grids.
- Geometric transformations.
- Line systems and diagrams.
- Shape language.
- Repeated patterns.
- Cutouts and masks.
- Negative-space reveals.

Use to explain relationships, structure, sequence and abstraction.

### 3. Editorial / documentary
- Archival photographs and documents.
- Map and timeline animation.
- Layered image planes.
- Crop and pan choreography.
- Annotation and marginalia.
- Paper, print and scan textures.
- Photo-to-diagram transitions.

Use when authenticity, evidence, history or human context matters. Do not invent historical images or imply illustrative material is documentary evidence.

### 4. Data storytelling
- Animated charts.
- Network graphs.
- Counters and numerical transformations.
- Maps and flows.
- Scale comparisons.
- Data-to-shape transformations.

Use only when data is accurate, sourced and legible. Do not decorate a scene with meaningless charts.

### 5. 3D and spatial graphics
- Product-like hero objects.
- Exploded views.
- Isometric environments.
- Dimensional typography.
- Architectural cutaways.
- Camera moves through spatial systems.
- Abstract material studies.

Use when depth, scale, spatial relationships or physicality adds meaning. Avoid 3D as a default because it is expensive and increases continuity risk.

### 6. Generative / procedural
- Particle fields.
- Flow fields.
- Parametric patterns.
- Noise-driven deformation.
- Cellular systems.
- Repeating simulations.
- Organic-to-geometric transformations.

Use when emergence, scale, complexity or transformation is part of the story. Keep particle counts and shader complexity hardware-aware.

### 7. Transitions
- Match cuts.
- Shape transformations.
- Mask wipes.
- Camera pushes and pulls.
- Parallax handoffs.
- Typography-led transitions.
- Graphic line continuity.
- Whip pans, only when tonally appropriate.

Transitions should connect ideas, not merely decorate scene boundaries.

## Technique selection test

Before implementing a technique, Claude must answer:
1. What does the viewer need to understand or feel?
2. Why is this technique better than a simpler alternative?
3. Which reference or design principle supports it?
4. What is the focal point?
5. What changes over time?
6. What stays fixed?
7. What is the intended timing and easing?
8. What is the hardware/rendering cost?
9. What would make the technique feel generic or clichéd?
10. How does it connect to the next scene?

If Claude cannot answer these, it should simplify or research further.

## Anti-patterns

Avoid:
- Stick figures as the default metaphor.
- Generic floating icons.
- Random gradients and glassmorphism without a concept.
- Endless particle backgrounds.
- Arbitrary 3D camera orbits.
- Text appearing word-by-word without narrative reason.
- Unmotivated zooms and pans.
- Generic HUDs, fake dashboards and decorative charts.
- Repeated transitions because they are easy to code.
- Inconsistent visual styles between scenes.
