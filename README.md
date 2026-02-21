# Personal Site (minimal black & white)

Static personal website with blog-ready structure.

## Local preview
From this folder:

```bash
python3 -m http.server 8080
```

Open: http://localhost:8080

## Structure
- `index.html` — homepage (skills/about/latest posts/contact)
- `styles.css` — minimalist styling
- `blog/index.html` — blog listing
- `blog/posts/*.html` — post pages

## Edit content
- Replace placeholder contact links/emails in `index.html`
- Add new blog posts under `blog/posts/` and list them in `blog/index.html`

## Hosting option recommended: GitHub Pages via `gh-pages` branch
See `DEPLOY.md`.
