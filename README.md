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

- **index.html** – Prototype of the ExMod console UI (shell, panels, toolbars, chat). The preview pane may embed the UPS article as an iframe.

## Usage

Open `html/index.html` in a browser to view the scaffolded page. The page is self-contained with embedded styles for easy experimentation.

## Provenance (for agent updates)

After implementing or refining the prototype, update this section:

| Aspect | Source | Notes |
|--------|--------|-------|
| **Derived from MHTML** | | DOM structure, Spectrum tokens, embedded CSS, class names |
| **Derived from HTML** | | Fallback structure, labels, region order |
| **Inferred from screenshots** | | Spacing, typography, colours, hierarchy |
| **Approximate** | | Regions that are placeholder or best-guess |
| **Replace with real app code** | | What should be swapped for production implementation |
