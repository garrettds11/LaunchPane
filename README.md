# LaunchPane

LaunchPane is a lightweight, single-file web launcher for organizing and opening web resources from a customizable dashboard.

It is designed to feel more like a personal application surface than a traditional bookmark page: resources are presented as app-style tiles, organized into groups, and stored in a portable JSON configuration.

## Highlights

- **Single static HTML file** — no build process, package manager, framework, or backend required.
- **Resource launcher** — add a name and URL, then open resources with a single click.
- **Favorites-first layout** — Favorites is always the top group.
- **Custom groups** — create, rename, reorder, collapse, and remove groups.
- **App-style icons**
  - automatically request a website favicon when online,
  - allow a custom icon URL,
  - provide built-in SVG icons,
  - fall back to locally generated vector icons when remote icons are unavailable.
- **Portable JSON configuration** — import and export the complete dashboard state.
- **Session storage** — edits are retained for the current browser session without requiring a server.
- **Custom appearance**
  - accent color,
  - RGB background color,
  - uploaded or URL-based background images,
  - configurable background shading overlay,
  - editable title and tagline.
- **Resource actions** — right-click a tile to edit, move, favorite, or delete it.
- **Responsive layout** — adapts from desktop through smaller viewport sizes.
- **Local-first operation** — most application behavior continues to work without a backend.

## Run LaunchPane

Clone the repository:

```bash
git clone https://github.com/garrettds11/LaunchPane.git
cd LaunchPane
```

Then open `index.html` in a modern browser.

No installation or build command is required.

You can also serve the directory with any static web server. For example:

```bash
python -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

## First Use

When LaunchPane opens, it prompts for an existing JSON configuration.

- Choose **Import JSON** to restore a previously exported dashboard.
- Choose **Skip for now** to begin with the default configuration.
- Add resources with the toolbar at the top of the page.
- Select a group before adding a resource to place the new link in that group.

Favorites remains the first group and is always expanded.

## Resource Icons

The icon picker beside the resource fields supports three modes:

1. **Automatic** — LaunchPane requests the website's favicon.
2. **Built-in** — choose from local SVG icons such as mail, book, ticket, document, shield, people, chart, cloud, code, and link.
3. **Custom URL** — provide an HTTP or HTTPS URL to an icon.

Automatic favicon lookup currently uses Google's favicon service. Remote icon failures automatically fall back to a locally rendered SVG icon, so a missing network resource does not break the tile.

## Configuration and Storage

LaunchPane treats the dashboard configuration as JSON.

The exported configuration includes:

- dashboard title and tagline,
- appearance settings,
- accent color,
- background settings,
- background image metadata or embedded image data,
- shading overlay,
- groups and their order,
- resource names and URLs,
- icon selections,
- creation and update timestamps,
- application/configuration metadata.

During normal use, the current state is written to browser `sessionStorage`.

Because `sessionStorage` is session-scoped, **export JSON when you want a durable backup or a configuration that can be moved to another browser or computer**.

Large uploaded background images may exceed a browser's storage quota. LaunchPane can still display the image for the current page session, but exporting the configuration is recommended if the browser cannot persist the full embedded image.

## Background Images

LaunchPane supports:

- common browser-readable image formats,
- uploaded local images,
- HTTP/HTTPS image URLs,
- relative image paths when served from a web server,
- solid RGB backgrounds when no image is selected.

Browsers do not expose the original local filesystem path of an uploaded file. When a local background image is selected, LaunchPane records the filename as metadata and embeds the image data in the configuration.

## GitHub Pages

Because LaunchPane is a static site with `index.html` at the repository root, it can be hosted directly with GitHub Pages.

In the repository:

1. Open **Settings → Pages**.
2. Choose **Deploy from a branch**.
3. Select the `main` branch and the repository root (`/`).
4. Save the Pages configuration.

## Privacy and Network Behavior

LaunchPane does not require a backend service for dashboard storage.

The application may make outbound requests when:

- automatic website icons are enabled,
- a custom remote icon URL is used,
- a remote background-image URL is configured,
- a resource tile is opened.

Dashboard configuration itself is stored in the browser session unless you explicitly export it.

## Repository Layout

```text
LaunchPane/
└── index.html
```

The application currently keeps its HTML, CSS, SVG generation logic, and JavaScript in one portable file.

## License

LaunchPane declares the **Creative Commons Attribution-NoDerivatives 4.0 International (CC BY-ND 4.0)** license.

You may copy and redistribute the unmodified work, including commercially, provided appropriate attribution is given. Redistribution of modified versions is not permitted under this license.

License details:

https://creativecommons.org/licenses/by-nd/4.0/

> CC BY-ND 4.0 is a Creative Commons content license and is not an OSI-approved open-source software license.

## Status

LaunchPane is under active refinement. Current work is focused on visual polish, responsive behavior, icon quality, and matching the intended glassmorphism / app-launcher design language while keeping the project dependency-free.
