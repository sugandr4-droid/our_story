# Sugand ❤️ Srinidhi — Our Story

A personal, single-page love story website. Fully static — no build step, no backend.

## Project structure

```
.
├── index.html          # the whole site
├── assets/
│   ├── photo-01.jpg ... photo-18.jpg   # gallery photos
│   └── song.mp3                        # background music (Marandhu Poche)
└── README.md
```

This was converted from a single self-contained HTML file (with everything
base64-embedded) into a normal static site: the photos and audio now live
as real files in `assets/`, and `index.html` just references them with
relative paths (`assets/photo-01.jpg`, `assets/song.mp3`, etc). This is
required for GitHub Pages / Vercel — a multi-megabyte single HTML file with
embedded base64 media works locally but is slow to load and awkward to
version-control, so splitting it out is the right move for real hosting.

Fonts (Google Fonts) and libraries (GSAP, Three.js) are loaded from public
CDNs, so there's nothing else to install.

## Deploy on GitHub Pages

1. Create a new **public** repo on GitHub (e.g. `our-story`).
2. Push this folder's contents to the `main` branch:
   ```bash
   git init
   git add .
   git commit -m "Our story"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```
3. In the repo, go to **Settings → Pages**.
4. Under **Build and deployment → Source**, choose **Deploy from a branch**.
5. Branch: `main`, folder: `/ (root)` → **Save**.
6. Wait a minute, then your site is live at:
   `https://<your-username>.github.io/<repo-name>/`

## Deploy on Vercel (usually faster, and gives a nicer URL)

**Option A — via GitHub (recommended):**
1. Push this repo to GitHub as above.
2. Go to [vercel.com](https://vercel.com) → **Add New… → Project**.
3. Import the GitHub repo.
4. Framework preset: choose **Other** (it's a plain static site — no build
   command, no output directory needed since `index.html` is at the root).
5. Click **Deploy**. You'll get a `https://<project-name>.vercel.app` URL.

**Option B — via CLI, no GitHub needed:**
```bash
npm install -g vercel
cd our-story        # this folder
vercel               # follow the prompts, choose defaults
vercel --prod        # promote to production URL
```

## Notes

- The `song.mp3` file is ~3.3 MB and the photos are a few hundred KB each —
  well within free-tier limits on both GitHub Pages and Vercel.
- If you ever want a custom domain (e.g. `oursweetstory.com`), both GitHub
  Pages and Vercel support it for free — you just point your domain's DNS
  at them and add the domain in the project settings.
- Everything is static, so there's no `.env`, no database, and nothing to
  configure server-side.
