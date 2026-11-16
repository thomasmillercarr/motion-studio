# 03 — Reference intelligence and visual knowledge base

## Why this is a core subsystem

The reference library is not a moodboard dumping ground. It is the external visual memory that helps Claude make better decisions.

The system must retrieve examples by:
- Visual technique.
- Motion behaviour.
- Composition.
- Typography.
- Transition.
- Material.
- Camera movement.
- Narrative function.
- Genre or use case.
- Technical implementation, where known.

A reference tagged only “documentary” or “3D” is not useful enough.

## Reference source strategy

Start with a small, high-quality source directory. Treat sources as discovery routes, not as guaranteed APIs or permission to scrape.

Suggested starting points:
- Motionographer — professional motion design, studios, projects and interviews.
- Stash — animation, motion design and VFX work.
- Art of the Title — title sequences and their creative context.
- Awwwards — interactive and web motion references; useful for interaction and transitions, not automatically film references.
- Codrops — inspectable web animation techniques and implementation experiments.
- Vimeo / studio portfolios — original project films and creator credits.
- Behance — portfolios and project case studies; quality varies, curate manually.
- GitHub motion-design repositories — reusable code, examples and implementation patterns.
- Motion Canvas examples — practical reference for the chosen 2D animation framework.

A source directory is maintained in `data/reference-sources.json`. Each source has:
- name
- base_url
- source_type
- useful_for
- access_method
- terms_or_license_notes
- enabled
- last_checked

## Research adapter design

Do not hard-code one paid search provider.

Create an interface with interchangeable providers:
- `manual`: user adds URLs or local files.
- `web_search`: uses a configured search provider or an IDE/browser capability.
- `browser`: opens public pages and extracts permitted metadata.
- `github`: searches public repositories and reads repository metadata.
- `local`: searches the existing vault.

For the MVP, implement `manual`, `local` and one research adapter that is actually available in the user's environment. If no web search credentials or browser capability exist, tell the user and provide search queries/links rather than claiming to have researched.

Do not use unofficial scraping to bypass logins, paywalls, robots rules or site terms. Respect rate limits. Do not download or redistribute protected videos. Save source links, permitted thumbnails or user-provided screenshots, and concise analysis notes. Keep creator attribution.

## Reference ingestion

Input types:
1. URL.
2. User-provided image or screenshot.
3. User-provided video clip, where rights permit analysis.
4. Local project file.
5. Public code repository.

Ingestion steps:
1. Validate source and record provenance.
2. Capture permitted metadata.
3. Generate a local thumbnail/contact sheet only from assets the user may store.
4. Ask Claude to analyse the visible design characteristics.
5. Add structured tags.
6. Save a compact analysis record.
7. Index tags and text in SQLite.
8. Mark uncertain or unviewable properties as unknown.

## Reference quality scoring

Score each reference 0–5:
- Craft: evidence of intentional design and execution.
- Relevance: useful for the current story/scene.
- Specificity: contains a clearly identifiable technique.
- Explainability: the technique can be described and adapted.
- Provenance: creator/source information is clear.
- Reproducibility: plausible to reproduce with the available stack.

Do not equate popularity with quality. A beautiful reference may be irrelevant or impossible to reproduce.

## Reference analysis schema

Store one JSON record per reference:

```json
{
  "id": "REF-0001",
  "title": "Project title",
  "creator": "Studio or artist",
  "source_url": "https://...",
  "source_type": "studio_portfolio",
  "date_added": "YYYY-MM-DD",
  "access_status": "viewed",
  "local_asset": null,
  "provenance_notes": "Public project page; no source video copied.",
  "visual_tags": [
    "kinetic_typography",
    "editorial_composition",
    "mask_reveal"
  ],
  "techniques": [
    {
      "name": "masked typographic reveal",
      "observed_behaviour": "Letters are revealed through a moving rectangular mask.",
      "timing": "staggered, moderate acceleration",
      "adaptation": "Use a similar reveal principle with original type layout and copy."
    }
  ],
  "composition": "Large headline aligned to a strict grid...",
  "palette": ["#111111", "#F2F0EA"],
  "motion_character": ["precise", "restrained"],
  "narrative_function": "introduces a key concept",
  "adaptable_principles": [
    "Use the mask to create a reveal rather than a generic fade."
  ],
  "do_not_copy": [
    "Exact layout, brand marks, footage or distinctive authored assets."
  ],
  "scores": {
    "craft": 5,
    "relevance": 4,
    "specificity": 4,
    "explainability": 5,
    "provenance": 5,
    "reproducibility": 4
  },
  "confidence": "medium",
  "notes": ""
}
```

## Retrieval behaviour

When the Creative Director requests references:
1. Search the local index first.
2. Return the best 5–10 records, not the entire database.
3. If local evidence is insufficient, perform external research.
4. Deduplicate by source URL and project.
5. Return a compact evidence pack with links and relevant extracted principles.
6. Ask Claude to compare references and propose a synthesis.

For MVP, SQLite FTS5 plus structured tag filtering is sufficient. Do not add vector databases or embeddings until the vault is large enough that keyword/tag retrieval demonstrably fails.

## Reference-to-design translation

Every selected reference must produce an explicit mapping:

| Reference observation | Adapted design rule | Scene use | Implementation |
|---|---|---|---|
| Type enters through a narrow mask | Reveal the key phrase through a moving aperture | Scene 1 | SVG clip path |
| Fine lines converge on a focal point | Use converging lines to visualise centralisation | Scene 2 | Canvas / SVG |
| Large negative space around one object | Keep the hero object isolated | Scene 3 | Layout tokens |

This prevents Claude from collecting attractive images without learning anything actionable.

## User reference intake

When the user supplies a reference:
- Ask what they like only if the reason is not obvious.
- Identify the specific property they may be responding to: timing, composition, typography, material, colour, camera, transition or emotional tone.
- Do not reproduce the entire reference.
- Search for adjacent references to avoid overfitting to one example.
- Record user-owned references separately from public research references.
