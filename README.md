# Personal site — Raghav Bharadwaj

Static, single page, no build step. `index.html` is the whole site.

---

## Deploy to GitHub Pages

You need a GitHub account. The repo must be **public** — Pages from a private repo requires a paid plan.

### 1. Create the repository

Go to <https://github.com/new>.

**Name it exactly `<your-username>.github.io`.**

If your username is `raghhav-bharadwaj`, the repo name is `raghhav-bharadwaj.github.io`. This is what gets you the clean root URL. Any other repo name puts the site at `username.github.io/repo-name/` instead.

- Visibility: **Public**
- Do **not** tick "Add a README" — it just gets in the way

Click **Create repository**.

### 2. Upload the files

On the empty repo page, click **uploading an existing file**.

Drag in:

- `index.html`
- `404.html`
- `robots.txt`

Commit straight to `main`.

### 3. Turn Pages on

**Settings → Pages** (left sidebar).

- Source: **Deploy from a branch**
- Branch: **main**, folder: **/ (root)**
- **Save**

First build takes 1–2 minutes. Your site is then live at:

```
https://<your-username>.github.io
```

The Pages panel shows the URL and a green tick once it's up. HTTPS is automatic.

---

## Prefer the command line?

```bash
cd portfolio-site
git init -b main
git add .
git commit -m "Personal site"
git remote add origin https://github.com/<your-username>/<your-username>.github.io.git
git push -u origin main
```

Then do step 3 above.

---

## Adding your CV as a download

The Contact section currently reads **"Available on request"** and opens an email. To serve the PDF directly instead:

1. Put your CV in this folder, named exactly `cv.pdf`
2. Open `index.html` and find `DEPLOY NOTE` (one occurrence, near the end)
3. Replace this line:

   ```html
   <a href="mailto:raghhavbharadwaj@gmail.com?subject=CV%20request">Available on request</a>
   <span class="note">Happy to send a PDF — just ask.</span>
   ```

   with:

   ```html
   <a href="cv.pdf" target="_blank" rel="noopener">Download CV (PDF)</a>
   ```

4. Commit and push. Pages redeploys in about a minute.

---

## Making edits later

Edit `index.html` and push — that's the entire workflow. Every change redeploys automatically.

Things you'll likely want to change first:

| What | Where to look |
|---|---|
| Job titles, dates, companies | `<ol class="timeline">` |
| Project write-ups | `<section id="projects">` |
| Skills | `<dl class="rows">` |
| Email, LinkedIn | search for `mailto:` and `linkedin.com` |
| Colours | the `:root` block at the top of `<style>` |
| Fonts | the Google Fonts `<link>` in `<head>` |

Colours are defined once as CSS variables in `:root`, with dark-mode values just below. Change `--accent` in both blocks to reskin the whole page.

---

## Notes

- **No dependencies.** The only external request is Google Fonts. If that ever fails, the page falls back to Georgia / system sans and still reads fine.
- **Dark mode** follows the visitor's OS setting automatically.
- **Custom domain** later: buy one, add a `CNAME` file containing just the domain, and point DNS at GitHub. Settings → Pages → Custom domain walks you through it. Nothing in `index.html` needs to change.
