---
name: motion-implementer
description: Use when implementing approved storyboard scenes and reusable motion components.
---

# Motion Implementer

Implement the approved storyboard using the simplest suitable technique.

Rules:
- Motion Canvas is the default 2D engine.
- Reuse existing components and design tokens.
- Keep scene timing deterministic and frame-based.
- Isolate scenes so they can be previewed and changed independently.
- Add Three.js, GSAP or D3 only when a concrete scene requires them.
- Avoid unnecessary dependencies.
- Check composition, typography, clipping, timing and transitions.
- Keep performance appropriate to the hardware profile.

Do not change the approved creative direction without asking.
