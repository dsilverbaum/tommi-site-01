# Technical bilingual consistency check

Date: 2026-02-22

## Scope checked
- FI/EN page parity (home, blog index, article pages)
- `hreflang` reciprocity and canonical consistency
- sitemap integrity vs actual files
- nav links and relative path correctness

## Findings
1. **Parity:** Core FI/EN structure exists for home, blog index, and two long-form articles.
2. **Broken EN path discovered:** `en/blog/posts/first-post.html` was referenced from:
   - `en/index.html`
   - `en/blog/index.html`
   - `blog/posts/ensimmainen-postaus.html` (hreflang + language switch)
   - `sitemap.xml`
   but the file did not exist.
3. **FI article nav anchors were local-only and invalid on article pages:**
   - `ai-liiketoiminnassa.html`
   - `asiakasportaali-hyodyt.html`
   used `#osaaminen`, `#about`, `#yhteys` even though those IDs only exist on the homepage.

## Fixes made
- Added missing file: `en/blog/posts/first-post.html`
  - Includes canonical, FI/EN hreflang pair, OG metadata, JSON-LD, and correct relative stylesheet/nav links.
- Fixed FI article navigation links:
  - `ai-liiketoiminnassa.html`: `#...` → `./#...`
  - `asiakasportaali-hyodyt.html`: `#...` → `./#...`

## Verification
- Local href/path integrity check across all HTML files reports **0 missing local targets**.
- `hreflang` pairs now resolve for all listed FI/EN content URLs in sitemap.
- Sitemap entries match existing files.

## Notes
- 404 pages are intentionally `noindex` and outside sitemap; acceptable.
- If desired later, `x-default` hreflang can be added site-wide as a refinement.
