# HTML Scaffolding Experiment

An experiment in scaffolding an HTML page to match reference screenshots. This is a **UI prototyping and visual-alignment task**, not a website migration.

## Claude Code Instructions

See **[CLAUDE.md](./CLAUDE.md)** for essential instructions. Full protocol: [AGENT_PROTOCOL.md](./AGENT_PROTOCOL.md).

## Reference

**Screenshots** (`screenshots/`):

- **content-view.png** – Article content in a focused view
- **page-view.png** – Full page including header, breadcrumbs, and article

Both depict a UPS press release article: *"UPS Accelerates Intra-Asia Trade With Capacity and Speed Enhancements to Its Air Network"*.

**HTML export** (`html/`): The content in this folder was **exported from the actual Experience Modernization UI** using Chrome’s “Save page as.” That export is the UI we want to restyle to match the screenshots. It may be incomplete because Chrome export does not reliably capture iframes or runtime state.

## Output

- **index.html** – Standalone prototype that replicates the layout and styling from the screenshots

## Usage

Open `html/index.html` in a browser to view the scaffolded page. The page is self-contained with embedded styles for easy experimentation.

## Provenance (for agent updates)

After implementing or refining the prototype, update this section:

| Aspect | Source | Notes |
|--------|--------|-------|
| **Derived from HTML** | | DOM structure, labels, region order, class names |
| **Inferred from screenshots** | | Spacing, typography, colours, hierarchy |
| **Approximate** | | Regions that are placeholder or best-guess |
| **Replace with real app code** | | What should be swapped for production implementation |
