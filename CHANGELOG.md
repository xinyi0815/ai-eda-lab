# Changelog

Notable changes to the AI-EDA Lab website. Newest first.

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
