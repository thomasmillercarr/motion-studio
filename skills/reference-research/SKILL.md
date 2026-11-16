---
name: reference-research
description: Find, analyse and file motion-design and visual references as compact evidence cards with sources, separating what was observed from what is interpreted. Searches the local vault first, then the web when a search tool exists. Use when a film or design needs reference evidence, when the user shares a reference link or image to add, or when asked what references back a creative choice.
---

# reference-research: evidence, not moodboards

A reference earns a place when it shows a **technique you can name** that serves a **story job**
you can name. Popularity is not evidence. A beautiful reference that the renderer cannot
reproduce, or that does a different job, is noise.

## Where cards live

`vault/cards/<ID>.md` in the working directory (create `vault/cards/` on first use). IDs are
`REF-` plus a short slug (`REF-artofthetitle-severance`). When working inside the motion-studio
repo, its `vault/` is the shared library. Without a working directory (Claude chat), keep cards in
the conversation and skip the vault step.

## Workflow

1. **Vault first.** Grep `vault/cards/` for the technique and story-job words (`mask reveal`,
   `match cut`, `kinetic type`, `data reveal`, `reveal on the drop`). Reuse good cards; do not re-research.
2. **Then the subject itself.** Their site, product UI, logo and voice (the studio skill needs these anyway).
3. **Then the web**, only if a search or fetch tool is available. Look for work by studios and
   title designers, case studies that explain decisions, and pages that let you see the work.
   Discovery routes: Art of the Title, Motionographer, Stash, studio portfolios, Vimeo staff picks,
   Codrops (web technique). These are routes to original work, not things to cite in their own right.
4. **Analyse only what you can see.** If you could only read a description, or the page blocked
   you, say so in `access`. Never describe a film you did not view as if you had.
   A text fetch of a page with video is `description only`. If no motion reference could be
   viewed, say so in the direction's Evidence rather than implying you watched it.
5. Stop at 6-10 cards for a film, 2-3 per direction (directions may share cards). Enough evidence to choose, not a survey.

## Card format (keep it under 25 lines)

```markdown
---
id: REF-slug
title: Project title
creator: Studio or person (credited as on the source)
url: https://…
accessed: YYYY-MM-DD
access: viewed | stills only | description only | blocked
tags: [kinetic-type, match-cut, editorial-grid, data-reveal, dark-to-light]
story_job: what the technique does for the viewer (introduce, contrast, reveal, prove, resolve)
---
**Observed** (what is on screen; timings only if you measured them):
- …
**Interpreted** (why it works; label guesses as guesses):
- …
**Principle to borrow** (one or two lines, stated generally):
- …
**Do not copy**: the layout, marks, footage, characters, type treatment or palette that make it theirs.
**Fit**: craft 0-5, relevance 0-5, reproducible in HTML/CSS/SVG 0-5
```

## Rules

- Record source and creator on every card. Never download, store or redistribute video, frames
  or artwork from a reference. Links and your own words only.
- Do not bypass logins, paywalls or robots rules. Follow each site's terms; fetch single pages,
  never crawl or bulk-download.
- Screenshots taken to view a reference are temporary. Never save them in `vault/` or the repo.
- Quote at most one sentence from a case study, in quotation marks, with the link.
- User-supplied reference images go in `films/<slug>/refs/` (private), never in `vault/`.
  `vault/` may be public.
- Principles transfer; looks do not. Every card says what is off limits.
- When you report back to studio, give a 2-3 line summary per card (id, principle, why it fits),
  not the cards' full text.
