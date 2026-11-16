# Existing motion-design skills and engines (survey, 2026-11-16)

GitHub search via `gh`. Each candidate was shallow-cloned to a scratch folder and read, but **none of their code was run and nothing was installed.** Star counts come from GitHub on 2026-11-16.

## Engines

| Repo | Stars | Licence | What it is | Fit |
|---|---|---|---|---|
| heygen-com/hyperframes | 85.0k | Apache-2.0 | HTML/CSS + seekable animation (GSAP) rendered to deterministic MP4. `hyperframes render` CLI; built for agents; Node ≥22 | **Strong candidate.** Renders unattended, so it can run as a GitHub Actions job. Opus is fluent in HTML/CSS. Ships a `remotion-to-hyperframes` skill. |
| remotion-dev/remotion | 73.6k | Remotion licence (free for a sole operator) | React video framework. Mature CLI and cloud rendering | **Strong candidate.** Most mature. The official skills are below. |
| Motion Canvas | n/a | MIT | Renders only from its editor UI | **Drop.** It can't be scheduled. |

## Skills worth extracting (principles, rewritten in our own words)

| Source | Licence | Extract | Why |
|---|---|---|---|
| hyperframes `motion-doctrine`, `cut-the-curve`, `seam-craft` | Apache-2.0 (keep NOTICE) | Vector law across cuts (exit determines entry), carrier elements, no idle wobble, stillness before the climax, seam-gate script | The best material found on *continuity between scenes*, which is the biggest gap in our spec |
| Tejashmakwana/motionmaxxing | Apache-2.0 | `references/` (idea, world, motion, transitions, type, slop, judgment), measured easing curves, `look.py`/`lint.mjs` render gates, the `taste/verdicts.md` pattern | Closest to our "every technique must earn its place" rule. Its PROVENANCE.md matches our reference-ethics rules (principles only, no copied frames). **Caveat:** one commit, 6 weeks old, unverified claims. |
| remotion-dev/skills (official) | see repo | `remotion-best-practices`, `-render`, `-captions`, `-multimedia` | Use these only if we pick Remotion. They're kept up to date with Remotion (v4.0.544). |
| iart-ai/motion-design-skills | MIT | `motion-art-direction`, `shot-composition`, `color-motion`, `beat-sync-editing` | Feeds our creative-direction and storyboard phases |
| LottieFiles/motion-design-skill | MIT | Timing/easing tables, choreography, Disney principles | A solid foundation, though written with UI motion in mind |
| bangtutorial/bang-motion | MIT | Cinematic GSAP patterns ("not a slideshow") | Written in Indonesian. Low priority. |
| kylezantos/design-motion-principles | MIT | Audit mode for spotting "AI-slop" motion | UI-interaction focus. Low priority. |

Index for later: zhuyansen/awesome-claude-video-skills (180 repos).

## Rules for extraction
- Extract principles into our own `skills/`. Don't install whole skill packs, because they come with competing pipelines and add a lot to context.
- Keep licence notices for Apache-2.0 sources and credit every source in the SKILL.md.
- Stars don't measure quality. Judge candidates by a rendered result from the same brief.
