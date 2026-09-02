# Changelog

Notable changes to the AI-EDA Lab website. Newest first.

## 2026-09-02 — fourth design pass: the editorial hybrid

Rebuilt from evidence instead of invention. A 21-agent survey read 16 real lab
websites (NTU EDA, Yao-Wen Chang, MiuLab, VLLab, Media IC, Cornell Zhang, MIT
HAN Lab, MIT EEMS, UCLA VAST, UCSD ABKGroup, ETH IIS, and six more discovered at
NTU/NYCU and abroad), scoring each for "AI-template feel". The finding was
unanimous: every site that reads as human is a dense editorial document — dated
news feed, flat citation lists, numbers inside sentences, white ground, whitespace
instead of section bands. Every site built from symmetric cards and tinted bands
scored worst, matching exactly what was rejected in v3.

- Homepage centerpiece is now a dated news feed (fixed crimson date column,
  hairline rules), seeded with 7 real events from 2024–2026: DATE 2026 and DAC
  2024 papers, the MLCAD 2025 Best Artifact Award, U.S. Patent 12,475,291,
  ICCAD 2024 contest prizes
- Key numbers moved into the opening sentences as prose with links; stat tiles,
  the per-year chart, the canvas circuit backdrop, tinted bands, cards, chips and
  accordions are all gone
- Publications render as year-ordered flat citation lines with inline crimson
  award annotations and [DOI] links
- Advisor block uses the survey's one sanctioned asymmetric gesture: portrait
  with a hard offset crimson shadow beside evidence-dense prose
- FAQ is a plain Q&A document in the professor's voice
- Footer gained human texture: bilingual address, map links, maintainer line, and
  a "Last built" date stamp
- Masthead is a plain non-sticky document header; nav is text links
- Accents now have disjoint jobs: indigo for structure (headings, links), crimson
  for time and honor (dates, awards, NEW badges, recruiting strip)

## 2026-09-01 — third design pass

Second pass corrected the first one's density but overshot into emptiness — the page
read as a document rather than a site, with no imagery, no footer and no contrast
between sections. Added substance without returning to the earlier visual noise.

- Full-bleed hero on a tinted ground with a generated routing/floorplan backdrop
  drawn on canvas (seeded, so it is stable across loads) and masked away from the text
- Sections alternate between plain and tinted full-bleed bands to give the page rhythm
- Added a dark footer with contact details, section links and outbound links — the
  page previously just stopped
- New chart on the publications page: papers per year, 2007–2026, stacked as
  DAC/ICCAD vs everything else, with legend, hover tooltip, keyboard focus and a
  table view. Palette checked with the data-viz validator: CVD ΔE 18.3, both steps
  clear 3:1 against their surface in light and dark
- Added a lab wordmark (inline SVG die-with-pins) in the header and footer
- Photo placeholders now use a hatched frame so they read as intentional
- Research headings carry an accent rule; key figures use the accent colour

## 2026-09-01 — second design pass

Rebuilt the visual treatment after feedback that the first pass read as grainy,
stiff and rough.

- Removed the hairline-grid mosaics and bordered cells; sections are now separated
  by whitespace, with rules kept only under section headings
- Dropped monospace type entirely — it was the main source of the "rough" feel
- New pairing: Source Serif 4 for headings, Source Sans 3 for everything else
- Body type up from 15px/1.6 to 16.5px/1.75; section spacing up from 44px to 84px
- Replaced the heavy left sidebar with a light sticky top bar
- Cut the second accent colour; one deep blue now carries the whole palette
- Added transitions on hover and view changes, with `prefers-reduced-motion` honoured

Content and data unchanged.

## 2026-09-01 — repository set up for GitHub Pages

- Moved `preview/index.html` to `index.html` so Pages can serve it from the root
- Added `robots.txt` (`Disallow: /`) and a `noindex` meta tag — **both must be
  removed before launch**, see README
- Added `.nojekyll` so GitHub Pages serves the files as-is
- Added README and this changelog

## 2026-08-31 — first draft

- Seven sections: home, research, publications, people, awards, join us, contact
- English default with a Chinese toggle
- Publication list generated from Prof. Lin's DBLP record (66 papers), sorted into
  top conference / journal / conference / preprint tiers
- Real content carried over from Prof. Lin's personal page: biography, 23 awards,
  9 US patents, 2 book chapters, the 10-question recruiting FAQ, contact details
- Fixed a duplicated phrase in the Chinese FAQ ("豐厚的研究津貼豐厚的研究津貼")
- Placeholders: student roster, alumni placements, photos, lab logo
- Research descriptions drafted from the publication record — **not yet reviewed
  by Prof. Lin**
