# SEO audit (FI + EN)

Date: 2026-02-22
Scope: FI and EN home, blog index, and article pages in this repo.

## Executive summary
Site basics are solid (titles, meta descriptions, canonicals, hreflang pairs on key pages). Biggest gains now come from:
1) stronger internal linking from articles,
2) metadata consistency between FI and EN article templates,
3) minor technical cleanups that reduce crawl ambiguity.

---

## Priority 1 (high impact, low risk)

### 1) Strengthen internal linking on article pages
**Issue:** Article pages had limited contextual links to other relevant pages, reducing crawl depth and topical cluster signals.

**Fix implemented:** Added “Lue seuraavaksi / Read next” sections to:
- `ai-liiketoiminnassa.html`
- `asiakasportaali-hyodyt.html`
- `blog/posts/ensimmainen-postaus.html`
- `en/ai-in-business.html`
- `en/b2b-customer-portal-benefits.html`
- `en/blog/posts/first-post.html`

**SEO value:** Better page-to-page authority flow, stronger topic cluster around AI + B2B customer process content, lower chance of orphan-like behavior for deeper pages.

### 2) Fix broken in-page navigation links on FI article templates
**Issue:** FI standalone article header links pointed to local anchors (`#osaaminen`, `#about`, `#yhteys`) that do not exist on article pages.

**Fix implemented:** Updated to homepage section URLs:
- `./#osaaminen`
- `./#about`
- `./#yhteys`

Files:
- `ai-liiketoiminnassa.html`
- `asiakasportaali-hyodyt.html`

**SEO value:** Better internal navigation and UX; less pogo behavior from dead nav targets.

### 3) Clean malformed list formatting in FI articles
**Issue:** Markdown bold markers (`**...**`) were rendered literally inside HTML list items.

**Fix implemented:** Replaced with semantic `<strong>...</strong>` in:
- `ai-liiketoiminnassa.html`
- `asiakasportaali-hyodyt.html`

**SEO value:** Cleaner rendered content and improved perceived quality/trust.

---

## Priority 2 (next sprint)

### 4) Standardize EN article metadata parity with FI pages
**Current gap:** EN article pages are missing some social and structured metadata seen in FI pages (e.g., Open Graph article fields, Twitter tags, Article JSON-LD on some EN templates).

**Recommended:** Add consistent metadata block on all EN articles:
- `meta name="author"`
- `og:type=article`, `og:title`, `og:description`, `og:url`
- `twitter:card`, `twitter:title`, `twitter:description`
- `Article`/`BlogPosting` JSON-LD with `datePublished`, `dateModified`, `author`, `inLanguage`

### 5) Add `hreflang="x-default"` on FI/EN pairs
**Current gap:** FI/EN alternates exist, but no x-default.

**Recommended:** Add `x-default` to FI primary (or language selector destination) across paired pages.

### 6) Unify article date presentation format by language
**Current gap:** EN pages show `21.2.2026` style.

**Recommended:** For EN use `2026-02-21` or `Feb 21, 2026` consistently in visible text and keep ISO dates in structured data.

---

## Priority 3 (content expansion)

### 7) Add one supporting article per topic cluster (FI + EN)
Suggested next pieces to reinforce topical authority:
- AI governance and responsible implementation (practical checklist)
- B2B customer portal rollout pitfalls and migration plan
- Foresight-to-execution operating model for leadership teams

Each new article should include:
- 2–4 contextual internal links to existing cluster pages
- reciprocal links from existing articles where relevant

---

## Observed strengths
- Clear, keyword-aligned titles and descriptions on core pages
- Canonicals present on FI + EN pages reviewed
- Hreflang pairing exists on key equivalents
- Logical, crawlable static architecture (no JS dependency for core content)

