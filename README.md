# Ribbon website

Help, FAQ, support, Privacy Policy and Terms of Use for the Ribbon iPhone app. Plain HTML and one stylesheet, with no scripts, cookies, web fonts or trackers.

| Page | Used for |
|---|---|
| `index.html` | Home / App Store marketing URL |
| `guide.html` | How to use Ribbon |
| `faq.html` | FAQ (linked from the app: Settings → About → Help & FAQ) |
| `support.html` | App Store **Support URL** |
| `privacy.html` | App Store **Privacy Policy URL** (also linked from the app) |
| `terms.html` | Terms of Use (also linked from the app) |

The app links to `https://finleyrayde-cell.github.io/ribbon/…`, so keep this repo named `ribbon` and the file names as they are.

## 1. Add the contact email
Every page uses the placeholder `CONTACT_EMAIL`. Replace it everywhere at once:

```sh
cd ~/Documents/Ribbon-website
sed -i '' 's/CONTACT_EMAIL/you@example.com/g' *.html
grep -c CONTACT_EMAIL *.html   # should print 0 for every file
```

## 2. Publish (free GitHub Pages needs a public repo)
```sh
gh repo edit finleyrayde-cell/ribbon --visibility public --accept-visibility-change-consequences
gh api -X POST repos/finleyrayde-cell/ribbon/pages -f "source[branch]=main" -f "source[path]=/"
```
After a minute or two it's live at https://finleyrayde-cell.github.io/ribbon/

## Editing
Edit the HTML directly. The header and footer are repeated on each page, so change all six if you change one. If the app's data handling ever changes (sync, analytics, anything online), update `privacy.html` **before** that version ships, and change its "Effective" date.

This repo only holds the website. The app's code is in the private `Purrpose` repo.
