# 00 — Product brief

## Product vision

Build a local-first, reference-led motion graphics studio in which Claude Code acts as a creative collaborator and implementation agent. The system should turn scripts and briefs into visually distinctive motion-design videos without defaulting to generic AI explainer aesthetics.

The differentiator is not merely code generation. It is **visual judgement supported by references**.

## Core problem

Claude can write animation code, but it often struggles with:
- Selecting an original visual concept for an abstract idea.
- Understanding what makes a reference visually effective.
- Translating a reference into composition, timing, hierarchy, material, camera and transition rules.
- Maintaining one coherent visual system across scenes.
- Knowing when a technique is inappropriate or visually clichéd.
- Iterating without wasting tokens and render time.

## Product principles

1. **Reference before invention.** Search the reference vault and research relevant work before proposing a direction.
2. **Direction before production.** The user approves a visual direction and representative frame before the system builds a full sequence.
3. **Technique must earn its place.** Never use a technique solely because it is available.
4. **Small engine, expandable adapters.** One dependable default renderer; specialist engines are optional.
5. **Human taste remains in the loop.** Claude proposes, explains and implements; the user directs and approves.
6. **Cache deterministic work.** Never ask an LLM to repeat a lookup, calculation, timestamp extraction or asset inventory that code can perform.
7. **Learn deliberately.** Improve reusable rules only after feedback is reviewed and generalised.
8. **Respect references.** Study and describe references; do not copy protected work, download assets unlawfully or present another artist's work as original.

## Users and use cases

Primary user: an individual creator working inside an IDE, who wants professional-looking motion graphics and needs Claude to do the technical implementation.

Initial use cases:
- Short documentary sequences.
- Educational / explanatory films.
- Editorial brand films.
- Data-led stories.
- Product and process explainers.
- Kinetic typography-led social videos.

## MVP non-goals

Do not initially build:
- A general-purpose nonlinear video editor.
- A cloud rendering service.
- A multi-user SaaS platform.
- An autonomous system that publishes videos.
- A large asset marketplace.
- Full 3D character animation.
- A dependency on paid stock libraries or image-generation APIs.
- A complex agent swarm.

## Success criteria

A user can provide a brief or script and receive:
1. A concise set of clarifying questions, only where needed.
2. A research-backed creative direction with reference links.
3. A storyboard and animatic.
4. A reviewable scene preview.
5. A finished MP4.
6. A reusable learning record from feedback.

Quality is measured by creative coherence and communication, not by number of effects, libraries or lines of code.
