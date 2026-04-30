# AGENTS.md

## Cursor Cloud specific instructions

This is a single-file static web application (`index.html`) — a NameMC clone for Minecraft player profile lookups.

### Running the development server

```bash
cd /workspace && python3 -m http.server 8080
```

The app is then accessible at `http://localhost:8080/`.

### Architecture notes

- **No build step, no package manager, no dependencies to install.** The entire application is self-contained in `index.html`.
- External libraries (skinview3d, Font Awesome, Google Fonts) are loaded via CDN at runtime.
- Player data is fetched client-side from `api.ashcon.app` (Mojang API proxy).
- OptiFine capes are fetched via `api.codetabs.com` CORS proxy; this degrades gracefully if unavailable.

### Testing

There are no automated tests. Manual testing is done by:
1. Serving the file with any HTTP server
2. Opening in a browser and searching for a Minecraft username (e.g. "Notch", "Dream")
3. Verifying the 3D skin viewer renders and profile data (UUID, name history, capes) loads

### Lint / Build

No linter or build tooling is configured. The project is vanilla HTML/CSS/JS.
