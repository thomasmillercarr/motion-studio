# 12 — Research sources and technical notes

This is a starting reading list, not an endorsement of every tool or a claim that every site offers unrestricted access. Check current documentation, licence terms and usage policies before implementation.

## Motion design reference discovery

- Motionographer: https://motionographer.com/
  - Professional motion design, studios, project features and interviews.
- Stash: https://www.stashmedia.tv/
  - Animation, motion design and VFX inspiration.
- Art of the Title: https://www.artofthetitle.com/
  - Title design and sequence analysis.
- Awwwards animation: https://www.awwwards.com/
  - Interactive and web motion references.
- Codrops: https://tympanus.net/codrops/
  - Experimental web animation techniques and code examples.
- Vimeo: https://vimeo.com/
  - Original work and creator/studio portfolios; respect access and rights.
- Behance: https://www.behance.net/
  - Portfolio and project discovery; manually curate quality.
- GitHub motion-design topic: https://github.com/topics/motion-design
  - Open-source implementation discovery.
- Awesome AI Motion Graphics: https://github.com/benjoox/awesome-ai-motion-graphics
  - Curated collection of tools, skills and workflows; verify each project's status and licence.
- Motion Canvas: https://motioncanvas.io/
  - Framework examples and technical patterns.

## Technical references

- Motion Canvas repository: https://github.com/motion-canvas/motion-canvas
  - MIT-licensed TypeScript animation library and editor; project describes a real-time preview and focus on vector animation/voiceover sync.
- Motion Canvas quickstart: https://motioncanvas.io/docs/quickstart/
  - Project setup and editor workflow.
- Motion Canvas rendering: https://motioncanvas.io/docs/rendering/
  - Preview/render settings, scale and frame-rate configuration.
- Motion Canvas FFmpeg exporter: https://motioncanvas.io/docs/rendering/video/
  - Video export integration; documentation notes the exporter is relatively new.
- Remotion performance: https://www.remotion.dev/docs/performance
  - Render performance and concurrency guidance.
- Remotion GPU: https://www.remotion.dev/docs/gpu
  - GPU acceleration considerations.
- Remotion GL options: https://www.remotion.dev/docs/gl-options
  - Renderer backends and software-rendering caveats.
- Three.js WebGLRenderer: https://threejs.org/docs/pages/WebGLRenderer.html
  - Renderer options, including low-power preference.

## Research notes that affect the build

1. Motion Canvas explicitly provides an editor with real-time preview and is designed for vector animation and voiceover synchronisation. This makes it a strong candidate for the lightweight 2D-first MVP.
2. Motion Canvas documentation describes its FFmpeg exporter as relatively new. Test export reliability in Phase 1 before committing the full pipeline.
3. Remotion documents rendering as a heavy workload and exposes concurrency controls. More concurrency is not automatically better on a low-memory machine.
4. Remotion documents GPU acceleration and software-rendering fallback behaviour. GPU-heavy effects can be significantly slower without a suitable GPU.
5. The project should benchmark on the actual target hardware rather than relying on generic hardware claims.

## Licensing checklist

Before adding a library, template, code sample, font, image, sound or video:
- Find the authoritative licence.
- Confirm commercial-use permissions if relevant.
- Check attribution and redistribution requirements.
- Record the licence and source URL.
- Keep reference-only material out of the final output unless licensed.
- Do not assume a GitHub repository is open source merely because it is public.
