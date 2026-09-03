# AI-EDA Lab — website

Website for the **AI-EDA Lab**, National Yang Ming Chiao Tung University
(advisor: Prof. Mark Po-Hung Lin / 林柏宏).

**Live at <https://xinyi0815.github.io/ai-eda-lab/>**

**Status: draft.** This is a review copy shown to Prof. Lin for feedback on design
and content. It is not the finished site. Search engines are blocked — see
[Before this goes live](#before-this-goes-live).

---

## Current state

Right now the whole site is a **single self-contained `index.html`**. Navigation
between sections and the English/Chinese switch both run in the browser. That is
fine for a review copy but is *not* what ships — see [Where this is going](#where-this-is-going).

```
index.html              the entire site, one file
assets/logo.jpg         the lab logo, recovered from a slide deck
data/publications.json  66 publications, generated from DBLP
robots.txt              blocks all crawlers while this is a draft
.nojekyll               tells GitHub Pages not to run Jekyll on this repo
```

## Before this goes live

Two things currently keep the draft out of Google. **Both must be removed when the
real site launches**, or it will never appear in search results:

1. `<meta name="robots" content="noindex, nofollow">` near the top of `index.html`
2. `Disallow: /` in `robots.txt`

## Editing content

Everything except the publication list is written directly in `index.html`.
Each piece of text exists twice, once per language:

```html
<p class="l-en">English text</p>
<p class="l-zh">中文內容</p>
```

CSS hides whichever language is not active. If you add a new sentence, add both
versions — a missing `l-zh` means the text simply vanishes in Chinese.

Structured content (patents, awards, FAQ) lives in JavaScript arrays at the bottom
of the file. To add an award, add one entry to `AWARDS`; the page rebuilds that
list on load.

## Attribution policy — what the lab page may claim

The lab site lists **only work led by AI-EDA Lab** (NYCU era). Papers co-advised
with other groups belong to those groups; Prof. Lin's pre-NYCU career belongs to
his personal record. Both are linked, never listed, so the lab never appears to
claim another group's output. The same rule governs awards: the Awards page keeps
lab/student achievements (MLCAD 2025 Best Artifact, ICCAD 2024 contest prizes);
the professor's personal honors stay on his profile page.

Which papers count as lab-led is decided by `data/lab-publications.json` — an
include list of exact titles. The first pass (2020+, no other faculty co-author,
10 papers) was drafted by heuristic and **needs Prof. Lin's confirmation**; to
add or remove a paper, edit that file and re-inject.

## Publications are generated, not typed

`data/publications.json` comes from Prof. Lin's DBLP record:

- DBLP profile: <https://dblp.org/pid/71/7353.html>
- Machine-readable source: <https://dblp.org/pid/71/7353.xml>

Papers are sorted into four tiers by venue:

| Tier | Venues | Count |
|------|--------|------:|
| Top conference | DAC, ICCAD | 20 |
| Journal | IEEE TCAD (15), Integration, TODAES, TVLSI, TASE, Microelectronics Journal | 21 |
| Conference | ASP-DAC, DATE, MLCAD, ISPD, SMACD, ECCTD, ISVLSI, SLIP, VLSI-DAT | 24 |
| Preprint | arXiv (CoRR) | 1 |

The tier list is a config value, not hard-coded logic. When a new paper is indexed
by DBLP, regenerating the JSON picks it up and files it automatically. Nobody
should ever be typing citations into this repo by hand.

Patents and book chapters are **not** in DBLP and are maintained by hand in
`index.html`.

## What still needs supplying

- English names, research topics and personal links for the 18 students now
  listed (Chinese names supplied 2026-09-03)
- For the 22 alumni now listed (confirmed via thesis records, 2026-09-03;
  the full working sheet is 參考資料/alumni-roster-draft.md, local-only and
  gitignored): **graduation year, thesis topic, and first placement** for each
  (placements are the most persuasive thing a lab site can show a prospective
  student)

**Alumni-row policy (set 2026-09-03):** each graduate's line carries the bare
paper/thesis title only — no venue names, awards, or author-position claims —
so no graduate overshadows another. Do not decorate individual alumni rows.
- Prof. Lin's photo

**Members-page policy (set 2026-09-03):** the advisor and the students are
separate pages (`v-advisor` / `v-members`); the members page splits Ph.D. /
M.S. / alumni; **no member photos are published** — some alumni may not want
theirs shown, so none are used until the lab decides otherwise. Do not re-add
photo boxes to member rows. **Ordering:** members are listed by seniority,
senior first, but the year level itself is deliberately NOT displayed anywhere
on the page — keep new names in seniority order without labeling it.
- **Confirmation that `assets/logo.jpg` is the current logo**, and a vector
  original (AI/SVG/EPS) if one exists — the file here was extracted from a slide
  deck, so it is raster and carries a baked-in background
- **Confirmation of the lab-publication curation** in `data/lab-publications.json`
- **Confirmation that the ICCAD 2024 contest teams were this lab's students**
- **Confirmation of the five research descriptions**, which were drafted from the
  publication record and have not been reviewed by Prof. Lin

## Where this is going

The plan agreed with the lab, once the design is signed off:

1. **Content moves into `data/*.json`.** HTML becomes templates. Day-to-day
   updates mean editing a JSON file, not markup.
2. **A build step (`build.js`) renders those templates to static HTML** before
   publishing. This matters: in the current draft the browser assembles the page,
   so a crawler that does not run JavaScript sees an empty shell. Generating the
   HTML ahead of time fixes that, without changing how content is edited.
3. **Two real language trees** — English at `/`, Chinese at `/zh/` — cross-linked
   with `hreflang`, instead of one page that swaps text.
4. **`sitemap.xml`, JSON-LD structured data and per-page titles**, generated by
   the same build.
5. **GitHub Actions** runs the build on push, so contributors only ever touch
   content.

No framework, no `npm install`, no dependencies to rot.

## Hosting

Currently served from this personal account for review. The intended home is the
`NYCU-AI-EDA` GitHub account (which already hosts
[Netlistify](https://github.com/NYCU-AI-EDA/Netlistify)), reached by
*Settings → General → Danger Zone → Transfer ownership* — this keeps the commit
history. A `*.nycu.edu.tw` subdomain can later be pointed at GitHub Pages with a
`CNAME` file plus one DNS record; nothing about the site needs to change.

## Committing

This repository is set to commit under a GitHub noreply address so no personal
mailbox ends up in the public history:

```sh
git config --local user.name  "xinyi0815"
git config --local user.email "137688174+xinyi0815@users.noreply.github.com"
```

`--local` keeps this to this repository. If the repo is later transferred to the
lab account, set the local identity to that account's own noreply address before
committing again.

## Local preview

No build step yet — open `index.html` in a browser, or:

```sh
python -m http.server 8000
```
