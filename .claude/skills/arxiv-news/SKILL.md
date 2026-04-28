---
name: arxiv-news
description: Add a news item about a new arXiv publication to the THK-AI website. Use whenever the user asks to announce a paper that has appeared on arXiv (e.g. "create a news post for the paper at arXiv:..."). Produces both DE and EN articles, wires them into news.qmd and both landing pages, and follows the established vekil/ + hatz26a/ pattern.
---

# Adding an arXiv news item

Use this procedure when announcing a new arXiv publication on the THK-AI site.

## Required inputs

Collect from the user (or the arXiv abstract):

- arXiv ID and URL (e.g. `2604.21991` / `https://arxiv.org/abs/2604.21991`).
- Authors with affiliations. Mark TH Köln authors clearly; link the TH Köln profile page if it exists.
- Title of the paper.
- Abstract.
- A **short ID** for the post — typically `<lastname-prefix><year-letter>` such as `veki26a`, `hatz26a`, `bart26g`. Use this as both the news subfolder name and the file stem.
- Source materials (LaTeX, figures) if available — usually placed by the user under `news/<short-id>/` before invocation.

If anything is missing, ask the user via AskUserQuestion before generating files.

## Directory layout

Two trees, both keyed by the short ID:

```
news/<short-id>/                          # editorial source: tex, refs, original PDFs
  <short-id>-<topic>.md                   # DE article
  <short-id>-<topic>-en.md                # EN article
figures/news/<short-id>/                  # web-renderable assets
  <slug>.png                              # the image used in the news/landing cards
```

Do not put the news card image inside `news/<short-id>/` — that folder is for source material only. The Markdown article references the PNG via a relative path `../../figures/news/<short-id>/<slug>.png`.

## Image preparation

Pick the most representative figure (often the teaser / first figure of the paper). If only PDF is available, convert with `pdftoppm` (already installed):

```
pdftoppm -png -r 150 news/<short-id>/<figure>.pdf figures/news/<short-id>/<slug>
mv figures/news/<short-id>/<slug>-1.png figures/news/<short-id>/<slug>.png   # drop the page suffix
```

Aim for a ~150 dpi PNG; resulting files are typically 100–500 KB. If the user supplies a PNG/JPG directly, use that unchanged.

## Article structure (both DE and EN)

Mirror the pattern in `news/vekil/veki26a-shortcuts.md` and `news/hatz26a/hatz26a-monet.md`. Each file has YAML frontmatter, an H1 identical to the title, the figure, the date in backticks, an intro paragraph with the arXiv link and authors, then four short prose sections, and a citation line.

DE frontmatter and skeleton:

```markdown
---
title: 'Paper „<Paper Title>" auf arXiv erschienen'
date: "YYYY-MM-DD"
---

# Paper „<Paper Title>" auf arXiv erschienen

![<short caption>](../../figures/news/<short-id>/<slug>.png){fig-alt="<descriptive alt text>"}

`<DD. Monat YYYY>`

Das Paper *<Paper Title>* ist auf arXiv veröffentlicht: [arXiv:<id>](https://arxiv.org/abs/<id>). Autoren sind <author list with TH Köln links and affiliations>.

## Hintergrund
…

## Fragestellung
…

## Vorgehen
…

## Ergebnisse
…

Zitation: <Authors> (<Year>). <Title>. [arXiv:<id>](https://arxiv.org/abs/<id>).
```

EN frontmatter and skeleton (note `lang: en`):

```markdown
---
title: 'Paper "<Paper Title>" published on arXiv'
date: "YYYY-MM-DD"
lang: en
---

# Paper "<Paper Title>" published on arXiv

![<short caption>](../../figures/news/<short-id>/<slug>.png){fig-alt="<descriptive alt text>"}

`YYYY-MM-DD`

The paper *<Paper Title>* has been published on arXiv: [arXiv:<id>](https://arxiv.org/abs/<id>). The authors are <author list>.

## Background
…

## Research question
…

## Approach
…

## Findings
…

Citation: <Authors> (<Year>). <Title>. [arXiv:<id>](https://arxiv.org/abs/<id>).
```

Style follows `CLAUDE.md`: flowing prose, sparing use of bold/em-dash/lists, German umlauts in DE body. The German visible date uses the long form (`28. April 2026`); the English visible date uses ISO (`2026-04-28`); both YAML `date:` fields stay ISO.

Translate the four sections directly between languages — do not let DE and EN drift apart in content.

## Wire-up edits

After creating the two article files, three top-level files must be updated:

1. **`news.qmd`** — insert a new `:::{.news-card}` block immediately after `:::{.news-grid}` so the entry appears at the top (newest first). Use the existing card pattern (image with `.news-card-image`, headline as link, date in backticks, one short paragraph, "Zum Beitrag" button). The link target is `news/<short-id>/<short-id>-<topic>.md`.

2. **`index.qmd`** (DE landing page) — the `:::{.feature-grid}` near the top shows the latest two news cards. Replace whichever card is now third-newest so the new arXiv item appears first. Use `### Headline` (not a link), date prefix `` `DD. Monat YYYY` -- `` and the "Zum Beitrag" button.

3. **`index-en.qmd`** (EN landing page) — mirror the same change with the EN article (`-en.md`), the EN headline, ISO date, and a "Read more" button. Per saved memory, the DE/EN landing pages must stay in sync within the same change set.

## Verification

- `quarto preview` and visually check: news card appears at the top of `news.qmd`, the landing pages show the new card as the first of two, the figure renders, and all links resolve.
- Confirm both DE and EN files compile without warnings about missing images or broken links.
- Sanity-check the citation line matches the arXiv metadata.

## Reference implementations

- `news/vekil/veki26a-shortcuts.md` and `news/vekil/veki26a-shortcuts-en.md` (with `news/vekil/veki26a.md` as an arXiv-confirmation stub).
- `news/hatz26a/hatz26a-monet.md` and `news/hatz26a/hatz26a-monet-en.md`.

When a future post deviates from this layout (different image source, missing English version, etc.), prefer to adjust this skill rather than work around it silently.
