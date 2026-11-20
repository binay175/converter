# Quick Converters — Edit & Publish Guide

Reference for updating the app and pushing changes live to GitHub Pages.

- **Live site:** https://binay175.github.io/converter/
- **Repo:** https://github.com/binay175/converter (public)
- **Local folder:** /Users/basabina/Documents/Projects/converterapp
- **Main file:** index.html (single self-contained file — HTML, CSS, and JS all in one)
- **Branch:** main
- **Commit identity (repo-local):** BinayB <binayb.app@gmail.com>

---

## Everyday edit loop

After changing `index.html`, publish with:

```bash
cd /Users/basabina/Documents/Projects/converterapp
git add index.html
git commit -m "Describe your change here"
git push
```

The live site at https://binay175.github.io/converter/ updates ~30–60 seconds
after the push. Do a hard refresh (Cmd+Shift+R) if you still see the old version
(browser cache).

### Authentication
On the first `git push`, macOS will prompt for credentials:
- **Username:** binay175
- **Password:** paste your GitHub Personal Access Token (PAT), NOT your account password

The macOS keychain remembers it after that, so future pushes won't prompt.

If you ever need a new PAT (e.g. the old one expired):
1. https://github.com/settings/personal-access-tokens/new
2. Resource owner: binay175 · Repository access: only "converter"
3. Repository permissions → Contents: Read and write
4. Generate, copy the `github_pat_...` value, use it as the password on next push.

---

## Useful commands

Check what changed before committing:
```bash
cd /Users/basabina/Documents/Projects/converterapp
git status
git -P diff
```

See recent history:
```bash
git -P log --oneline -n 20
```

Preview locally before pushing (open in browser, or serve for phone testing):
```bash
# Just open the file:
open index.html

# Or serve it for testing on your phone (same Wi-Fi):
python3 -m http.server 8000
# then on phone: http://<your-mac-ip>:8000   (find IP with: ipconfig getifaddr en0)
```

---

## One-time setup (already done — for reference only)

These were run once to connect this folder to GitHub. You do NOT need to repeat them.

```bash
git init
git config user.email "binayb.app@gmail.com"
git config user.name "BinayB"
git add index.html
git commit -m "Add Quick Converters app"
git branch -M main
git remote add origin https://github.com/binay175/converter.git
git push -u origin main
```

GitHub Pages was enabled via: repo → Settings → Pages → Source: "Deploy from a
branch" → Branch: main, folder / (root). (Requires the repo to be public on the
free plan.)

---

## Notes
- The app is 100% client-side: no backend, no data collected, works offline.
- The published site is public (anyone with the link can use it). The free
  GitHub Pages tier does not support private/access-restricted sites.
- To restrict access to a specific group for free, migrate to Cloudflare Pages
  + Cloudflare Access, or serve over a Tailscale private network.
