# Vampics — self-hosting guide

## 1. Host the site (GitHub Pages)

1. Create a **public** repo on GitHub, e.g. `vampics`.
2. Upload everything in this folder: `index.html`, `support.js`, and the `assets/` folder.
3. Repo → **Settings → Pages** → Source: *Deploy from a branch* → branch `main`, folder `/ (root)` → Save.
4. After ~1 minute your site is live at `https://YOURNAME.github.io/vampics/`.
5. On your phone: open it in Safari → Share → **Add to Home Screen**. It opens fullscreen like an app.

## 2. Host your chapter PDFs

1. Create a second **public** repo, e.g. `vampics-library`.
2. Upload your PDFs (`Chapter_0.pdf`, `Chapter_1.pdf`, ...), a `cover.jpg`, and the `manifest.json` from the `library/` folder here.
   - Edit `"to": 200` in the manifest to match your last chapter number.
   - GitHub's web uploader takes ~100 files at a time (25 MB max each — your chapters fit). For bulk upload, use [GitHub Desktop](https://desktop.github.com).
   - **Size limit:** a repo should stay under ~1 GB. 200 chapters at ~15 MB is ~3 GB, so split them across repos (e.g. `vampics-library-1` ch 0–60, `vampics-library-2` ch 61–120, ...). Each repo gets its own `manifest.json` with the same `"id": "solo-leveling"` and its own chapter range — Vampics merges them into one series automatically.

## 3. Connect the library to Vampics

1. Open your Vampics site → sign in → **Settings → Account → Personal library**.
2. Paste the raw URL of each library repo, comma-separated:
   ```
   https://raw.githubusercontent.com/YOURNAME/vampics-library-1/main, https://raw.githubusercontent.com/YOURNAME/vampics-library-2/main
   ```
3. Click **Save & load library**. Your series appears on the home page under **"Your Library"** — click it and read. PDFs are rendered page-by-page right in the reader.

## Manifest format

```json
{
  "series": [{
    "id": "solo-leveling",
    "title": "Solo Leveling",
    "cover": "cover.jpg",
    "path": "optional/subfolder",
    "chapters": { "pattern": "Chapter_{n}.pdf", "from": 0, "to": 60 }
  }]
}
```

`chapters` can also be an explicit list: `[{ "num": 0, "file": "Chapter_0.pdf", "title": "Prologue" }, ...]`
 
