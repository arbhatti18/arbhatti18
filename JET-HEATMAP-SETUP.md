# GitHub Jet Heatmap — Setup Guide

Generates an animated `dark.svg` / `light.svg` heatmap of your contributions, adapted for **arbhatti18**.

## 1. Clone the generator repo
```bash
git clone https://github.com/Sushmitadasari/Sushmitadasari.git jet-heatmap-generator
cd jet-heatmap-generator
```

## 2. Install dependencies
```bash
npm install
```

## 3. Create a GitHub Personal Access Token
GitHub → **Settings → Developer settings → Personal access tokens** → Generate new token, with only:
- ✅ `read:user`
- ✅ `public_repo` (public repos)
- ✅ `repo` (only if your profile repo is private)

Do **not** grant `delete_repo`, `workflow`, or `admin:org`.

## 4. Generate the SVGs

**macOS / Linux (zsh/bash)**
```bash
export GH_USERNAME="arbhatti18"
export GH_TOKEN="YOUR_GITHUB_TOKEN"
node generate.mjs
```

**Windows (PowerShell)**
```powershell
$env:GH_USERNAME="arbhatti18"
$env:GH_TOKEN="YOUR_GITHUB_TOKEN"
node generate.mjs
```

## 5. Verify output
You should now have `dark.svg` and `light.svg` (or under `dist/`).

## 6. Copy into your profile repo and push
```bash
cp dark.svg light.svg ../arbhatti18/
cd ../arbhatti18
git add dark.svg light.svg
git commit -m "Add GitHub Jet Heatmap animation"
git push
```

## 7. Already wired into README.md
The "🔥 Jet Heatmap" section in `README.md` already references:
```
https://raw.githubusercontent.com/arbhatti18/arbhatti18/main/dark.svg
https://raw.githubusercontent.com/arbhatti18/arbhatti18/main/light.svg
```
Once `dark.svg` / `light.svg` exist on your `main` branch, it renders automatically — nothing else to change.

**Regenerating later:** re-run step 4 any time you want a fresh snapshot, then commit + push again. If you want it to stay current automatically, wrap steps 4–6 in a scheduled GitHub Action (same pattern as `workflows/snake.yml` and `workflows/profile-3d-contrib.yml`).
