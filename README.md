# Josh Command Center

A personal, installable web app — your tasks and daily command center — that runs on your iPhone and desktop, syncs through your own private GitHub repo, and works offline.

## What's in this folder
- `index.html` — the app
- `manifest.webmanifest` — makes it installable (Add to Home Screen)
- `sw.js` — service worker for offline use
- `icon-180/192/512.png` — app icons

---

## Setup (about 10 minutes, one time)

### 1. Create the app repo (public — holds the app, no secrets)
1. Go to https://github.com/new
2. Name it `command-center` → **Public** → Create.
3. Upload **all the files in this folder** (drag them into the repo's "Add file → Upload files").
4. Repo → **Settings → Pages** → Source: **Deploy from a branch** → Branch: `main` / `/ (root)` → Save.
5. After a minute, Pages gives you a URL like `https://YOURNAME.github.io/command-center/`. That's your app.

### 2. Create the data repo (private — holds your tasks)
1. Go to https://github.com/new
2. Name it `command-center-data` → **Private** → Create.
3. That's it — the app creates `tasks.json` automatically on first sync.

### 3. Create a fine-grained access token (lets the app save your tasks)
1. https://github.com/settings/tokens?type=beta → **Generate new token**.
2. Name: `command-center` · Expiration: your choice (e.g. 1 year).
3. **Repository access → Only select repositories →** `command-center-data`.
4. **Permissions → Repository permissions → Contents → Read and write**.
5. Generate, then **copy the token** (starts with `github_pat_`).

> The token lives only on your device (in the browser). It is never stored in any repo.

### 4. Put it on your iPhone
1. Open your Pages URL in **Safari** on your iPhone.
2. Tap **Share → Add to Home Screen**. It now opens like a native app.
3. Open it → tap the **⚙ gear** → enter:
   - Repo owner: your GitHub username
   - Repo name: `command-center-data`
   - File path: `tasks.json`
   - Token: the `github_pat_…` you copied
   - **Save & sync**.
4. Repeat step 3 on your desktop (any browser) using the same details. Both devices now sync.

---

## Using it
- **Add a task:** type in the box. Shortcuts: end with `tod` / `tmrw` / `mon`–`sun` / `6/14` for a due date, and `!high` / `!med` / `!low` for priority (or tap the colored dot).
- **Complete:** tap the circle. **Delete:** tap the ×.
- **Tabs:** Today (incl. overdue) · This week · No date · All open · Done.
- **Sync status:** the pill top-right — green = synced, amber = saving, red = error. Tap it to force a sync.
- **Offline:** works with no signal; changes sync next time you're online.

## The Apple Reminders / Siri flow
Keep Siri as your fast capture: "Hey Siri, remind me to…". Those land in Apple Reminders, and your `life-update` routine sweeps them into this app's task list so nothing's lost — while the Command Center stays the place you actually triage.

## Desktop bonus
Opened inside the Claude desktop app, the Command Center also shows live **calendar, email, and project** feeds under your tasks. On the phone it's the focused task app.
