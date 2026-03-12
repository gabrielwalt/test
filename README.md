# HTML Scaffolding Experiment

An experiment in scaffolding an HTML page to match reference screenshots. This is a **UI prototyping and visual-alignment task**, not a website migration.

## Claude Code Instructions

See **[CLAUDE.md](./CLAUDE.md)** for essential instructions. Full protocol: [AGENT_PROTOCOL.md](./AGENT_PROTOCOL.md).

## Reference

**Screenshots** (`screenshots/`):

- **content-view.png** – ExMod UI with content-focused view
- **page-view.png** – ExMod UI with full page layout

Both show the **ExMod console** (header, nav, Task Progress, Preview panel). The preview pane displays a UPS article inside an iframe—that is **not** the styling target.

**Exports** (`html/`): Two captures from the **actual Experience Modernization UI**:

- **MHTML** (`aemcoder.adobe.io.mht`) – Single-file capture with embedded CSS, Spectrum design tokens, and iframe content. **Preferred** for DOM structure and styling.
- **Chrome “Save page as”** (`Adobe Experience Manager.html`, `Adobe Experience Manager_files/`) – HTML + separate files. Fallback.

**Target:** **Only** the **ExMod console UI**—the frame that surrounds everything. Totally ignore the preview iframe content (no UPS article, no page load) and document view content. Build only the surrounding UI: header, nav, panels, toolbars, borders. The preview iframe should be empty or a minimal placeholder.

## Output

- **`html/index.html`** – Self-contained prototype of the ExMod console UI shell. The preview pane is an empty placeholder (no iframe content loaded).

## Usage

Open `html/index.html` in a browser to view the prototype. The page is self-contained with all styles embedded for easy experimentation. Best viewed at 1440x900 or wider.

## Provenance

| Aspect | Source | Notes |
|--------|--------|-------|
| **Derived from MHTML** | Color tokens (`--spectrum-gray-*` scale), layout approach (CSS Grid `minmax(400px, 33%) 1fr`), border radii (`0.625rem`, `1rem`), border colours (`#dadada`, `#e1e1e1`), font stacks (adobe-clean family), ProdNav collapsed width, chat panel structure, document tree structure, progress bar, viewport toggles | Extracted from `aemcoder.adobe.io.mht` embedded CSS and DOM |
| **Derived from HTML** | Adobe logo SVG path (`adobe-logo.svg`), region labels ("Task Progress", "Request support") | Taken from `Adobe Experience Manager_files/` |
| **Inferred from screenshots** | Overall proportions (~33/67% panel split), header height (~56px), nav width (~48px), spacing (20px grid padding), "Open in editor" button style (blue pill), task list indicators (blue/yellow/grey circles), chat message card styling, toolbar button order | Measured from `content-view.png` and `page-view.png` |
| **Approximate** | SVG icon paths (simplified Spectrum icon approximations), chat message placeholder text, task list item descriptions, document tree file names, progress bar percentage | Representative placeholders to show panel structure |
| **Replace with real app code** | All SVG icons (use Spectrum icon set), font loading (adobe-clean webfont), React component tree, interactive behaviour (accordion, collapse, viewport switching, chat input), real data binding, dark mode support | Static prototype — no interactivity or real data |
