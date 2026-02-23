# Personal Site (minimal black & white)

Static personal website with blog-ready structure.

## Local preview
From this folder:

```bash
python3 -m http.server 8080
```

Open: http://localhost:8080

## Structure
- `index.html` — Finnish homepage
- `blog/index.html` — Finnish blog listing
- `blog/posts/*.html` — Finnish post pages
- `en/index.html` — English homepage
- `en/blog/index.html` — English blog listing
- `en/blog/posts/*.html` — English post pages
- `styles.css` — shared minimalist styling

## Language workflow (FI + EN)
- Finnish is the source of truth.
- Every Finnish content update gets a matching English update in the `en/` side.
- Keep URL pairs aligned (example: `ai-liiketoiminnassa.html` ↔ `en/ai-in-business.html`).

## Edit content
- Replace placeholder contact links/emails in `index.html`
- Add new blog posts under `blog/posts/` and list them in `blog/index.html`

## Hosting option recommended: GitHub Pages via `gh-pages` branch
See `DEPLOY.md`.
