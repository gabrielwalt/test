# Claude Code Instructions

**Primary instructions for Claude Code working on this project.** Full protocol: [AGENT_PROTOCOL.md](./AGENT_PROTOCOL.md).

---

## Source Provenance

The `html/` folder contains exports from the **actual Experience Modernization UI**:

- **MHTML** (`html/aemcoder.adobe.io.mht`) – Single-file capture with embedded CSS, Spectrum design tokens, and iframe content. **Preferred** for DOM structure, class names, and styling reference.
- **Chrome “Save page as”** (`Adobe Experience Manager.html`, `Adobe Experience Manager_files/`) – HTML + separate files. May be incomplete; use as fallback.

---

## Essential Rules

1. **Screenshots are visual source of truth.** `screenshots/content-view.png` and `screenshots/page-view.png` define the target appearance of the **ExMod console UI**.
2. **MHTML is the best structural reference.** Use it for DOM hierarchy, Spectrum tokens, embedded CSS, and panel layout. Extract from it; do not confuse it with the preview content inside the iframe.
3. **When HTML/MHTML and screenshots conflict, prefer screenshots.**

---

## Task

Style **only** the **Experience Modernization Console UI**—the frame and chrome that surround everything. Nothing else.

**Scope:** You need **only** the UI that surrounds the content. You do **not** need:
- The page loaded inside the preview iframe (e.g. the UPS article)
- The document view content (document list, article preview, etc.)
- Any content that appears *inside* panels—only the panels themselves, their toolbars, borders, and layout

**Target:** The frame only—global header, left nav sidebar, Task Progress panel (with its UI, not the chat content), Preview panel (toolbar, document tree chrome, iframe *frame*). The preview iframe should be empty or a minimal placeholder (e.g. grey box). Totally ignore whatever would load inside it.

---

## Workflow

1. **Analyse** the ExMod UI from the screenshots: identify header, toolbars, panels, iframes, and what is common between the two views. Parse the MHTML to extract DOM structure, Spectrum tokens, and embedded CSS for the **shell** (ignore iframe content).
2. **Plan** before changing anything (assumptions, missing info, approximations).
3. **Implement** in the simplest maintainable way.
4. **Critique** against screenshots and refine.

---

## Do Not

- **Include or style any content inside the preview iframe.** Totally ignore it. No UPS article, no document view content, no page load. The iframe is just an empty frame. A previous run mistakenly produced a UPS article page—do not repeat that.
- Run migration, import, or design-migration workflows.
- Optimise for EDS, CMS, or content modelling.
- Overwrite unrelated files.

---

## Do

- **Use the MHTML** (`html/aemcoder.adobe.io.mht`) as the primary structural and styling reference: DOM hierarchy, Spectrum class names, `--spectrum-*` design tokens, embedded CSS (ChatPage, ContentPanel, treeBuilders, CodePanel).
- Use `Adobe Experience Manager.html` as fallback for structure and assets.
- Use screenshots for: spacing, typography, colours, hierarchy, alignment of the **console UI**.
- Focus on regions common to both screenshots (content-view and page-view).
- Keep changes isolated and reversible.
- Update README provenance table after implementation.

---

## Reference Files

| File | Purpose |
|------|---------|
| `html/aemcoder.adobe.io.mht` | MHTML capture: DOM, Spectrum tokens, embedded CSS for ExMod shell |
| [AGENT_PROTOCOL.md](./AGENT_PROTOCOL.md) | Full workflow, constraints, execution strategy |
| [README.md](./README.md) | Project overview, provenance table |
