# Stitched Together — website

A simple one-page site for Stitched Together, built with plain HTML/CSS/JS so it can be hosted for free on GitHub Pages with no build tools required.

## What's in here

```
index.html          the whole site (one page, with anchor sections)
styles.css           all styling
script.js            mobile menu + signup form handling
CNAME                tells GitHub Pages to serve the site at stitchedtogethernhl.com
images/
  logo.png            your logo, cut from the sticker artwork
  favicon-*.png        browser tab icon, a few sizes
  gallery/
    hat-1.jpg … hat-6.jpg      "What we make" photos (placeholders — replace these)
    town-1.jpg … town-4.jpg    "Sunday Stitch" local photos (placeholders — replace these)
```

## 1. Add your own photos

I couldn't include your actual photos since they weren't part of what you shared with me. Right now, every photo on the site is a placeholder with a dashed border that says "ADD PHOTO."

To swap them in: rename your photo files to exactly match the placeholder names above (for example, your best hat photo becomes `hat-1.jpg`) and drop them into `images/gallery/`, overwriting the placeholder. Keep using `.jpg` — if your file is a `.png` or `.heic`, either convert it or update the filename reference in `index.html` to match.

Tips for a good result:
- The `hat-` photos crop to a **square**. Photos of a single item (a hat laid flat, a pair of mittens) usually work better than wide group shots.
- The `town-` photos crop to a **4:3 landscape**. Street scenes, the river, storefronts, or meetup photos all work well.
- You can use more or fewer than 6/4 photos — just add or remove `<figure>` blocks in `index.html` inside the `#make` and `#stitch` sections, and keep the filenames in `images/gallery/` matching.

## 2. The signup form

The "Join the community" section embeds your existing Google Form directly in the page, so people can sign up without leaving the site. Submissions land wherever your Google Form is already set up to send them (its linked Google Sheet, and/or email notifications if you've turned those on in the form's settings).

If you ever swap in a different Google Form, update the URL in two places in `index.html`, inside the `#join` section:
- the `iframe src="…"` (add `?embedded=true` to the end of the form's normal URL)
- the fallback link right below it (the form's normal share URL, no `embedded=true`)

On some phones, embedded Google Forms scroll awkwardly inside the small iframe box — the "Open the signup form in a new tab" link underneath the embed is there as a fallback if that happens.

## 3. Put it on GitHub Pages

1. Create a new GitHub repository (public repos get free Pages hosting).
2. Upload everything in this folder to the repository — either by dragging the files into the GitHub web UI, or via git:
   ```
   git init
   git add .
   git commit -m "Stitched Together website"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPO.git
   git push -u origin main
   ```
3. In the repo, go to **Settings → Pages**.
4. Under "Build and deployment," set **Source** to "Deploy from a branch," branch `main`, folder `/ (root)`. Save.
5. GitHub will give you a URL like `https://YOUR-USERNAME.github.io/YOUR-REPO/` — the site is live there within a minute or two.

## 4. Connect stitchedtogethernhl.com

The `CNAME` file in this folder already tells GitHub to serve the site at `stitchedtogethernhl.com` — you don't need to create or edit it.

You do need to point your domain at GitHub, at wherever you bought `stitchedtogethernhl.com` (GoDaddy, Namecheap, etc.):

1. Add these four **A records** for the root domain (`@`):
   ```
   185.199.108.153
   185.199.109.153
   185.199.110.153
   185.199.111.153
   ```
2. Add a **CNAME record** for `www` pointing to `YOUR-USERNAME.github.io`.
3. Back in your repo's **Settings → Pages**, enter `stitchedtogethernhl.com` in the "Custom domain" field and save (this should already match the CNAME file). Once DNS propagates (can take up to a day), check "Enforce HTTPS."

Full GitHub docs, if anything looks different from what you see: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site

## Editing text or colors later

Everything is in plain HTML and CSS — no build step. Open `index.html` in any text editor to change wording, and `styles.css` to change colors (they're all defined as variables at the top of the file, e.g. `--teal`, `--berry`, `--gold`) or spacing. Save, and push the change to GitHub the same way you did in step 3 — the live site updates automatically.