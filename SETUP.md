# Profile Setup — Master Guide

Your profile repo must be named **`arbhatti18/arbhatti18`** (a repo with the exact same name as your username) — that's what makes GitHub render it on your profile page.

## File placement
```
arbhatti18/
├── README.md
├── assets/
│   └── hero-banner.svg
├── .github/
│   └── workflows/
│       ├── snake.yml
│       └── profile-3d-contrib.yml
├── dark.svg              ← added later via Jet Heatmap
├── light.svg              ← added later via Jet Heatmap
└── JET-HEATMAP-SETUP.md
```

Move the two workflow files from `workflows/` into `.github/workflows/` — GitHub only picks up Actions from that exact path.

## 1. Hero banner (already animated, no setup needed)
`assets/hero-banner.svg` is a self-contained animated SVG (gradient shift, floating glow orbs, fade-in title, pulsing subtitle). Nothing to run — it animates the moment it loads, since the animation is baked into the SVG itself.

## 2. Contribution Snake
1. Copy `workflows/snake.yml` into `.github/workflows/snake.yml`.
2. Push it. It runs automatically at midnight UTC and on manual trigger.
3. It publishes to an `output` branch — go to **Settings → Actions → General** and make sure "Read and write permissions" is enabled for the workflow token, or the push step will fail.
4. First run: **Actions tab → Generate Snake Animation → Run workflow** to generate it immediately rather than waiting for the schedule.

## 3. 3D Contribution Graph
1. Copy `workflows/profile-3d-contrib.yml` into `.github/workflows/profile-3d-contrib.yml`.
2. Push it, then trigger it once manually from the Actions tab.
3. It creates a `profile-3d-contrib/` folder with the SVG that `README.md` already links to.

## 4. Jet Heatmap
Follow `JET-HEATMAP-SETUP.md` — it's a one-time local script run (or automate it the same way as steps 2–3 above if you want it to refresh on a schedule).

## 5. Stats, streak, trophies, quote
No setup needed — these are all live-rendered from public GitHub API services (`github-readme-stats`, `github-readme-streak-stats`, `github-profile-trophy`, `quotes-github-readme`) and update automatically every time your profile page is viewed.

## Order of operations
1. Push `README.md` + `assets/hero-banner.svg` first — the page already looks good with just this.
2. Add the two workflows, run them manually once each.
3. Run the Jet Heatmap generator locally and push `dark.svg` / `light.svg`.
4. Done — everything after this refreshes itself (nightly Actions + live badge APIs).
