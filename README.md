# anmolsinghsethi.com

Source for my personal/academic homepage. Plain HTML/CSS/JS, no build step,
hosted on GitHub Pages with a custom domain from Namecheap.

## Before pushing

- Replace `YOUR_GITHUB_USERNAME` in `index.html` with your actual GitHub username (two places).
- Drop a square photo into this folder named `headshot.jpg` (optional — the page hides it gracefully if missing).
- Drop your resume PDF into this folder named `resume.pdf` (optional — remove the link in `index.html` if you skip it).

## 1. Push this repo to GitHub

```bash
cd ~/anmolsinghsethi-homepage
git init
git add .
git commit -m "Initial homepage"
git branch -M main
git remote add origin https://github.com/YOUR_GITHUB_USERNAME/anmolsinghsethi.com.git
git push -u origin main
```

(Create the empty repo on github.com first — name it whatever you like, e.g. `anmolsinghsethi.com`.)

## 2. Turn on GitHub Pages

1. On GitHub, go to the repo's **Settings → Pages**.
2. Under "Build and deployment", set **Source** to `Deploy from a branch`.
3. Branch: `main`, folder: `/ (root)`. Save.
4. Under "Custom domain", enter `anmolsinghsethi.com` and save. (The `CNAME` file
   already in this repo does this for you too — GitHub will pick it up automatically.)
5. Leave "Enforce HTTPS" checked once it becomes available (takes a few minutes
   after DNS is set up in step 3).

## 3. Point your Namecheap domain at GitHub Pages

In Namecheap: **Domain List → anmolsinghsethi.com → Manage → Advanced DNS**.

Delete any existing A/CNAME/URL Redirect records for `@` and `www`, then add:

| Type | Host | Value | TTL |
|---|---|---|---|
| A Record | @ | 185.199.108.153 | Automatic |
| A Record | @ | 185.199.109.153 | Automatic |
| A Record | @ | 185.199.110.153 | Automatic |
| A Record | @ | 185.199.111.153 | Automatic |
| CNAME Record | www | YOUR_GITHUB_USERNAME.github.io. | Automatic |

These four A records are GitHub Pages' fixed IPs — same for everyone, no need
to look them up per-account. DNS propagation usually takes anywhere from a
few minutes to a few hours.

## 4. Verify

- `https://anmolsinghsethi.com` should load the site.
- `https://www.anmolsinghsethi.com` should redirect to the same place.
- If GitHub shows a "DNS check unsuccessful" warning right after setting the
  custom domain, wait for DNS to propagate and re-save the custom domain field.

## Updating the site later

Edit `index.html` / `style.css`, then:

```bash
git add .
git commit -m "Update content"
git push
```

GitHub Pages redeploys automatically within a minute or two.
