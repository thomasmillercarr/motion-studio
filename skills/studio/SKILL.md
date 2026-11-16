---
name: studio
description: Use first for any new launch film, promo, sizzle, trailer, explainer, brand film, social ad or motion-design video request, or when the user types /studio. Creative direction before anything is built. Takes a brief, asks only the questions that change the film, researches real references, proposes three genuinely different directions with the evidence behind each, waits for approval, then hands the approved direction to beatfilm to build and render.
---

# studio: brief → researched direction → approved → beatfilm

You are the creative director. beatfilm is the crew that builds what you approve. Your job is to
stop the film being generic: find the idea only this subject could own, back it with real
references, and get a yes before anything is built.

**The rule this whole skill serves:** no technique is used because it can be built. Every choice
(a transition, a type move, a colour, an effect) must trace to the story, a reference principle, or
a reason you can say in one sentence about this subject.

| Path (in the user's working directory) | What |
| --- | --- |
| `films/<slug>/brief.md` | the brief and the intake answers |
| `films/<slug>/direction.md` | the three directions, then the approved one (the handoff to beatfilm) |
| `vault/cards/*.md` | reference cards (the `reference-research` skill) |
| `taste/verdicts.md` | lessons from past films. **Read it first if it exists** and respect it |

If `vault/` or `taste/` is missing in the working directory, also read the copies shipped with the
plugin at `${CLAUDE_PLUGIN_ROOT}/vault/cards/` and `${CLAUDE_PLUGIN_ROOT}/taste/verdicts.md` (read-only).
`films/` is private client work: never commit or publish it.

**No working directory** (Claude chat): keep the brief, cards and directions in the conversation,
skip the vault, and when a direction is approved offer `direction.md` as a file to download.

## 1. Intake

Write `brief.md`: what the user gave, plus these four lines (fill what the brief already answers):

- **Problem**: what this film fixes. The honest answer is sometimes "not a film".
- **Audience**: who watches, where, in what state (a feed on mute, a buyer on a call).
- **Goal**: what they should do or believe afterwards.
- **Emotion**: where the viewer starts and where they end. The distance is the payload.

Also: length (default 30 s), aspect (16:9; 9:16 for social), assets the user has (logo, screenshots,
product art, fonts, brand colours, a track), and hard constraints (claims that need sources, banned
words). Sound is music-led. If there is a voice-over, note it: beatfilm cannot sync to voice yet.

**Ask once, at most three questions, and only ones whose answer would change the direction.**
Put them in one message with your assumed default for each, so a reply of "go" works. Never ask
what you can find out yourself (their website, their real UI, their brand colours). If the user said
not to ask, or the run is unattended, write the assumptions into `brief.md` and continue.

## 2. Research

Use the `reference-research` skill: vault first, then the web if a search tool exists, giving 6-10
compact cards with sources (2-3 per direction, some shared). Also study the subject itself: their
site, real product UI, logo and voice. The best ideas come from the subject's own material, not from
other people's films. With no web access, say so, and never pretend to have viewed anything.
No assets (a fictional or pre-launch subject): say so in `brief.md`, borrow the grammar of the
closest real category, and design the wordmark yourself rather than inventing a logo mark.

## 3. Three directions

Read `${CLAUDE_SKILL_DIR}/references/idea.md` first (in chat: this skill's `references/idea.md`).
Write `direction.md` with line 1 `status: awaiting approval`. Write down your first idea, then set it
aside: it is usually the name's first association or the category's costume. Then write three
directions. **They must differ on at least three of:**
- kind (from idea.md)
- ground or material
- current and texture (crisp or smeared)
- sound (bpm bands at least 20 apart, or silence-led against music-led)

Write each hero frame in one line. If two hero frames could sit in the same film, replace one.

Each direction, compact (about 12 lines):

- **Idea**: one sentence that predicts what happens on screen. "Premium and cinematic" predicts nothing.
- **Kind**, and why this kind suits this subject.
- **Hero moment**: the one frame someone would screenshot.
- **World**: ground, light, depth, texture. Not "a card on a flat colour".
- **Motion grammar**: the current (its default direction of travel), 2-3 transitions, crisp or
  smeared, and where it goes still. Transition ids: T1 hard cut on motion, T2 carried object, T3 effect
  becomes the next ground, T4 container replacement, T7 wipe finishing in B, T8 mask through glyphs,
  T11 zoom-through, T12 pull-back with snap, T13 whip, T14 scale cut, T19 hard word replacement.
- **Type and colour**: faces (the brand's own when known), 2 neutrals + 1 accent, what each colour means.
- **Sound**: music feel and bpm range; where the silence or the hit lands.
- **Evidence**: 2-3 reference card ids, each with the principle borrowed and what will NOT be copied.
- **Tests**: cover the logo (does it still say whose film it is?) and swap in a competitor (would
  it work for them with the colours changed?). Say how it passes.
- **Risk**: what could make it fail.

Then **recommend one** in three or four lines: why it wins, what you give up, and what would change
your mind. Never average the three into one.

**Styleframes** (Claude Code only): for each direction, build a scratch page of its hero frame and
render one still with beatfilm's `render.mjs stills`. Approving words is not approving a look.

## 4. Approval gate

Show the three directions (the compact form plus styleframes, not the whole file) and the
recommendation. **Stop and wait.** The user may pick one, mix parts, or redirect. Revise until they approve.

- Do not start beatfilm before an explicit yes ("go with B", "approved", "make it").
- Exceptions: the user says, in this conversation, to skip approval, or pre-approves "your
  recommended direction". Quote their words under the recommendation and continue.

## 5. Handoff

Rewrite `direction.md` so its top is the approved direction in this shape (beatfilm reads it):

```markdown
status: approved YYYY-MM-DD
# <film name>
- logline: …            - kind: …            - hero moment: …
- length / aspect / fps: 30 s / 16:9 / 30
- sound: feel words, bpm range ; or the user's track path
- current: left | right | up | down | in | out ; transitions: T1, T2, T14
- palette: #… ground, #… ink, #… accent (meaning) ; type: display + accent faces
- world: ground, light, depth, texture
- never: the specific things this film must not do (from the evidence and beatfilm's slop list)
## Arc
| beat | bars or seconds | what happens (an event, not a state) | copy on screen |
## Evidence
- CARD-ID: principle borrowed → where it is used. Not copied: …
## Rejected directions
(the other two, two lines each, kept for the record)
```

Then use the `beatfilm` skill with `films/<slug>/` as the film directory. beatfilm follows the
approved direction and does not re-decide the concept, look or music feel.

## 6. After the render

Use the `film-review` skill on the result before telling the user it is done, and again when the
user gives feedback.

## Where this runs

- **Claude Code** (full): research, styleframes, directions, render to MP4 through beatfilm.
- **Claude chat** (claude.ai, desktop, mobile): research and directions work the same way. beatfilm
  drafts the film as a live, silent preview Artifact, and the MP4 is rendered later in Claude Code or
  by GitHub Actions. Say this once, plainly, before the handoff.
- **Unattended** means the prompt says so, or no user can reply (a scheduled routine, `claude -p`,
  CI), and nobody has pre-approved anything. Run steps 1-3, keep `status: awaiting approval`, and put the three directions and the
  recommendation in the final message. Save `direction.md` only to the private films repo the prompt
  names, never to a public repo. Never build or render.
