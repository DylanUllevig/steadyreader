# Steady Reader

A reading aid for someone who loses their place at the start of lines after a stroke. The whole app is in `index.html`; the other files make it installable as a phone or PC app and let it work offline.

## Files

| File | Purpose |
|---|---|
| `index.html` | The app |
| `manifest.webmanifest` | App name, icon and full-screen mode for "Add to Home Screen" / "Install" |
| `sw.js` | Offline cache. The page checks GitHub for updates on every launch and falls back to the cached copy when offline |
| `icons/` | Home-screen and browser icons |
| `lang/eng-data.js` | English text-recognition data for "Photo of a page" (about 3.9 MB), so photos work without downloading it from another site |

## Put it on GitHub Pages

1. Create a new **public** repository, e.g. `steady-reader`. Pages on a private repo needs a paid GitHub plan.
2. Upload everything in this folder to the root of the repo, keeping the `icons/` and `lang/` folders. In the web UI: **Add file → Upload files**, drag the folder contents in, then commit.
3. **Settings → Pages → Build and deployment**: Source **Deploy from a branch**, branch **main**, folder **/ (root)** → Save.
4. Wait a minute or two. The site will be at `https://<your-username>.github.io/steady-reader/`.

The address must be `https://` (GitHub Pages always is). Installing and offline use don't work over plain `http://` or from a file opened on disk.

## Install it on his phone

Open the URL on his phone first, then:

- **iPhone:** in **Safari**, tap **Share → Add to Home Screen → Add**. Safari is the most reliable route on iPhone.
- **Android:** in **Chrome**, tap the **⋮ menu → Add to Home screen → Install**.

Then open it **from the new home-screen icon** and go through setup there. Choose the first option on the setup screen. The installed app keeps its own storage, separate from the browser tab. Setup done in the tab won't carry over.

## Install it on his PC

Recommended: open the same URL in **Edge** or **Chrome** and click the **install icon** at the right end of the address bar (or find **Install** in the browser's menu). It gets a desktop/Start-menu icon, opens in its own window, updates automatically and works offline.

Fallback: double-click `index.html` from a folder on his PC. It works, but it won't update by itself. Opening PDFs and Word files, and reading photos, need an internet connection because the helper code downloads each time.

## Updating

Replace `index.html` in the repo and commit. Installed copies pick up the new version the next time they're opened with an internet connection, and the change takes effect on that launch.

If you change any other file (icons, `lang/`), also change `CACHE = 'steady-reader-v1'` in `sw.js` to `v2` etc. That makes devices fetch the new files.

## Things to know

- **His reading list, saved place and settings live on each device separately.** The phone and the PC don't sync.
- **Nothing he opens is uploaded.** Files are read in the browser on that device. GitHub only serves the app itself.
- **Read to me** uses the device's built-in voices. Quality varies; on iPhone, Settings → Accessibility → Spoken Content → Voices lets you download better ones.
