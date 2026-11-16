---
name: film-review
description: Review a rendered or previewed motion-design film honestly against its approved direction and the never-ship list, then log the user's feedback and propose lessons without silently turning one comment into a rule. Use after beatfilm renders, when the user gives feedback on a film, or when asked to critique a motion-design video.
---

# film-review: look before you say it is done

A film you did not look at is not finished. Review from the stills sheet and the preview, not
from the code.

## 1. Self-review (before telling the user it is done)

Inputs: `films/<slug>/direction.md`, `out/sheet.jpg` (from beatfilm's `render.mjs stills`), and the
render or the preview. Open the sheet and look. Then answer each line in one sentence in
`films/<slug>/review.md`.

**Gates (any FAIL is fixed, never explained away):**
1. `render.mjs check` passed, and the output exists and plays (dimensions, length, audio).
2. No page chrome: no film name in a corner, scene numbers, timecodes, bpm text, progress bars, corner brackets.
3. No invented stats, quotes, users or claims the brief did not give.
4. The final mark holds 0.6-1.4 s, with at most 3 new words beyond the name. No web-footer ending
   (logo + tagline + button + URL).
5. Every on-screen phrase is readable: on screen for at least 0.25 s per word + 0.4 s, and nothing
   important under 28 px on the page's long edge.

**Tests (questions, answered honestly):**
- **Direction**: is this the approved idea, hero moment and world, or did it drift to a default?
- **Slide test**: cover the text on the sheet. If more than half the frames are a flat colour with a card on it, it is a deck. (When the
  subject's own material is plain text, judge scale, density and camera instead.)
- **Pause test**: at any second, is something meaningful mid-flight, or is it waiting?
- **Seams**: does each cut carry something across (an object, a direction, a ground), keep the eye
  where it was, and land on a beat? Are there crossfades between scenes?
- **Effects spent once**: are flashes, shakes and springs each used once or twice, on a cause?
- **Cover the logo**: does it still say whose film it is?
- **Never list**: the "never" line in `direction.md`, and beatfilm's `references/slop.md` (load the
  beatfilm skill to read it). If that file is unavailable, the gates and tests above stand on their own.

Fix what fails, re-run `stills` on what changed, and record what you changed. Tell the user what
you could not fix.

**Chat draft** (no renderer): you cannot see frames. Check what you can from the code and the plan
(forbidden APIs, reading times, the never list). Give the user 5-8 timestamps to scrub, with what
should be on screen at each. Mark gate 1 "pending (render)", never PASS.

## 2. User feedback

Record each note in `review.md` with its time or scene, the note in the user's words, and a class:

| Class | Example | Where it goes |
| --- | --- | --- |
| this film only | "make the logo bigger here" | fix it; it stays in `review.md` |
| this client | "they never use dark grounds" | the film's `brief.md`; carry it into this client's next brief |
| general taste | "every film holds the end card too long" | **propose** a line for `taste/verdicts.md` |
| skill defect | "the cuts are always a beat late" | **propose** a change to the skill or script, with the evidence |

**Never promote a note to `taste/verdicts.md` or a skill without the user's yes.** Propose promotion
when a note has come up in two films, or when the user says it is a rule. Keep lessons general: no
client names or confidential details in `taste/verdicts.md`, because it may be public.

`taste/verdicts.md` entry format: `- YYYY-MM-DD: the lesson, as an instruction. (seen in N films)`
