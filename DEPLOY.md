# Deploy & host publicly (step-by-step)

## Option A — GitHub Pages (recommended first)

Works well for this static site and gives a public URL quickly.

### 1) Create a dedicated repo (public)
From local machine:
```bash
cd ~/Projects
mkdir tommi-site && cd tommi-site
# copy files from projects/personal-site/* here
```

Create GitHub repo (public):
```bash
gh repo create tommi-site --public --source=. --remote=origin --push
```

### 2) Publish with GitHub Pages
Quickest is `gh-pages` branch:
```bash
git checkout --orphan gh-pages
git add .
git commit -m "Deploy site"
git push -u origin gh-pages --force
```

Then in GitHub repo settings:
- Settings → Pages
- Source: `Deploy from a branch`
- Branch: `gh-pages` / root

Site URL becomes:
`https://<your-username>.github.io/tommi-site/`

### 3) Custom domain (optional)
- Add `CNAME` file with your domain
- Point DNS to GitHub Pages

---

## Option B — Host from Raspberry Pi (self-host)

Best when you want full control.

### 1) Install Caddy
```bash
sudo apt update
sudo apt install -y caddy
```

### 2) Copy site files
Place site under e.g.:
`/var/www/tommi-site`

### 3) Caddyfile
```caddy
yourdomain.com {
  root * /var/www/tommi-site
  file_server
}
```

### 4) Reload
```bash
sudo systemctl reload caddy
```

### 5) Expose safely
Use Cloudflare Tunnel if no open ports wanted.

---

## Recommendation
1) Launch fast with GitHub Pages.
2) Move to Pi hosting later only if you need full custom backend/control.

---

## Current automation in this workspace

This workspace now has an auto-publish flow for this project:

- Script: `scripts/publish-personal-site.sh`
- Trigger: `.githooks/post-commit`

Behavior:
- When a commit includes files under `projects/personal-site/`, the hook runs the publish script.
- Script syncs `projects/personal-site/` to `dsilverbaum/tommi-site-01`.
- Pushes `main` and then force-syncs `gh-pages` from `main` (GitHub Pages source branch).

Manual run (if needed):
```bash
/home/tommi/.openclaw/workspace/scripts/publish-personal-site.sh
```
