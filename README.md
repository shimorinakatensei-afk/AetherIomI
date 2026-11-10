# Aether by IOMI Roman & Co.

Aether is a focused study timer and personal study tracker designed around one idea: make it easier to begin, sustain, and review a focused study session.

The interface uses a restrained, system-font-first visual style. The application runs in the browser and stores its study data locally.

## Features

- **Focus timer** with 25, 45, 60, and 90-minute presets.
- **Custom duration picker** with a slider, live preview, and an explicit apply action.
- **Stopwatch** and **clock** modes.
- **Study subjects** with quick selection and custom subject creation.
- **Session records** with subject, duration, timestamp, study streak, and session mode.
- **Daily focus totals** and a per-subject breakdown.
- **Personal study streak** and recent-study information.
- **Record management**, including deletion, clearing the archive, and copying a text summary.
- **Themes**, optional completion sounds, fullscreen mode, and keyboard shortcuts.
- **Responsive layout** for desktop, tablet, and mobile screens.

Aether does not include a social leaderboard or shared-user ranking system.

## Getting started

Aether is a static browser application. There is no package installation or build step in this repository.

### Option 1: Open the file

Open `index.html` in a modern browser. Depending on browser settings, some `file://` storage behavior may vary; using a local web server is recommended.

### Option 2: Run a local server

From the repository root, run:

```bash
python -m http.server 8000
```

Then open [http://localhost:8000](http://localhost:8000).

You can also use the Live Server extension in Visual Studio Code.

## Keyboard shortcuts

| Shortcut | Action |
|---|---|
| `Space` | Start or pause the active timer / tracking mode |
| `R` | Reset the timer or stopwatch |
| `F` | Toggle fullscreen |
| `Esc` | Close open overlays |

Keyboard shortcuts are ignored while an input field is focused.

## Data and privacy

Aether stores application data in the browser's `localStorage` under the key `aether_study_state_v2`. It can also read the previous `aether_study_state_v1` key for compatibility.

The locally stored information includes:

- Scholar display name.
- Current and custom study subjects.
- Theme and sound preferences.
- Study streak and last-study metadata.
- Saved study-session records (up to 100 records).
- Current-day study time totals grouped by subject.

There is no application backend, account system, cloud synchronization, or application-level analytics integration in this version. Study records are not intentionally transmitted by the application to a server.

The page currently loads Tailwind CSS and Lucide icons from public CDNs. Those providers receive normal browser requests for these assets; see [PRIVACY.md](PRIVACY.md) for details.

Data is specific to the browser and origin where Aether runs. It is not automatically synced across devices. Clearing the browser's site data or local storage can delete saved records. A manual record-summary copy action is available, but automated backup and CSV export are not currently implemented.

## Technology

- HTML5
- CSS (including custom properties and responsive media queries)
- Vanilla JavaScript
- Tailwind CSS Play CDN
- Lucide icons via CDN
- Browser `localStorage`
- Web Audio API for synthesized interface sounds

## Project structure

```text
Aether-by-IOMI-Roman-and-Co/
├── index.html
├── README.md
├── CHANGELOG.md
├── CONTRIBUTING.md
├── PRIVACY.md
├── SECURITY.md
├── .gitignore
└── docs/
    ├── ARCHITECTURE.md
    └── DEPLOYMENT.md
```

## Deploy with GitHub Pages

1. Create a public GitHub repository (for example, `aether-by-iomi-roman-and-co`).
2. Upload or push the contents of this folder to the repository's `main` branch.
3. Open **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Select branch `main` and folder `/ (root)`, then save.
6. Wait for GitHub Pages to publish the site and open the URL shown in the Pages settings.

A detailed checklist is available in [docs/DEPLOYMENT.md](docs/DEPLOYMENT.md).

## Current limitations

- Data is stored locally in one browser profile; there is no account or cross-device sync.
- There is no CSV export or automatic backup/restore flow yet.
- In-progress timer state is not persisted as a resumable timer across page reloads.
- The application currently uses CDN-hosted Tailwind and Lucide assets, so the first page load requires internet access for the full styling and icon set.
- Tailwind's browser CDN is convenient for a lightweight static prototype. For a production build, consider compiling and pinning the CSS dependencies locally.
- If the selected subject changes during an active session, daily totals follow the subject selected at each tick, while the saved archive entry uses the subject selected when the session is saved. Keep the subject constant during a session for consistent attribution.
- Study duration is a measure of time while the app's tracking control is active. It cannot verify that the user is actually studying.

## License

No open-source license has been selected for this repository yet. Public visibility on GitHub does not itself grant permission to reuse, modify, or redistribute the source. Add a license only after the project owner chooses the intended terms.

## Project identity

**Aether by IOMI Roman & Co.**
