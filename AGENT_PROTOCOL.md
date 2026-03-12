# Experience Modernization Agent Protocol (Adapted)

**Entry point for Claude Code:** [CLAUDE.md](./CLAUDE.md)

**Purpose:** Guide the Experience Modernization Agent to make the HTML prototype fit the reference screenshots. This is a **UI prototyping and visual-alignment task**, not a website migration.

---

## Operating Mode

- **Start in Plan mode only.** Do not run any normal website migration workflow.
- **Do not assume** this is a source website to import into EDS or any CMS.
- **Treat this as** a UI prototyping and visual-alignment task for an existing HTML scaffold.

---

## Source Handling

**Provenance:** The `html/` folder contains two exports from the **actual Experience Modernization UI**:

1. **MHTML** (`html/aemcoder.adobe.io.mht`) – Single-file capture. Contains embedded CSS, Spectrum design tokens (`--spectrum-*`), full rendered DOM, and iframe content. **Preferred** for structure and styling.
2. **Chrome “Save page as”** (`Adobe Experience Manager.html`, `Adobe Experience Manager_files/`) – HTML + separate files. May be incomplete; use as fallback.

| Source | Role | Trust Level |
|--------|------|-------------|
| **Screenshots** (`screenshots/content-view.png`, `screenshots/page-view.png`) | Visual source of truth for the **ExMod console UI** | High – spacing, proportions, colours, hierarchy, typography |
| **MHTML** (`html/aemcoder.adobe.io.mht`) | Primary structural and styling reference: DOM, Spectrum tokens, embedded CSS (ChatPage, ContentPanel, treeBuilders, CodePanel) | High for structure; cross-check with screenshots |
| **HTML export** (`Adobe Experience Manager.html`, `_files/`) | Fallback structural reference | Low – may be incomplete |
| **HTML prototype** (`html/index.html`) | Current implementation | Target of improvement |

**Decision rule:** When HTML/MHTML and screenshots conflict, **prefer screenshots**.

**Ignore completely:** The preview iframe content, the document view content, and any page that would load inside panels. You need **only** the frame—the UI that surrounds it all. Extract from MHTML/HTML only the shell elements: header, left nav, Task Progress panel, Preview panel toolbar and document tree. The preview iframe should be empty or a minimal placeholder.

---

## Goal

Produce a rapid prototype that makes the **Experience Modernization Console UI** (the application shell) look and behave as close as practical to the attached target screenshots.

**Target = the frame only.** You need **only** the UI that surrounds everything—not the content inside. Totally ignore:
- The preview iframe content (no UPS article, no page load)
- The document view content (document list, article preview, etc.)
- Any content that appears *inside* panels

A previous agent mistakenly built a UPS article page. Do **not** repeat that. Build only the frame: header, nav, panels, toolbars, borders, layout. The preview iframe should be empty or a minimal placeholder (e.g. grey box).

**Focus on:** layout, hierarchy, spacing, typography, borders, backgrounds, panel structure, interaction affordances of the **console UI**.

---

## Required Workflow

### 1. Analyse

- Analyse the screenshots to understand the **ExMod UI structure**: header, toolbars, panels, iframes. Distinguish the **shell** from the **preview content** (UPS article) inside the right panel.
- Identify **common regions** between `content-view.png` and `page-view.png` (these are the stable shell elements).
- Parse the **MHTML** (`html/aemcoder.adobe.io.mht`): extract DOM structure, Spectrum tokens (`--spectrum-*`), and embedded CSS for the shell. Ignore the iframe’s inner content.
- Compare with `Adobe Experience Manager.html` as fallback: which parts can be reused, which must be reconstructed from screenshots.

### 2. Plan

- Produce a short implementation plan before making changes.
- Explicitly list:
  - **Assumptions**
  - **Missing information**
  - **Limitations** (e.g. iframe content, embedded previews)
  - **Regions that will be approximated** rather than derived

### 3. Implement

- Implement the prototype in the simplest maintainable way.
- Keep changes isolated and reversible.

### 4. Critique

- Perform a critique pass against the screenshots.
- Refine the result.

---

## Constraints

- **Do not** execute bulk import, page migration, design migration, navigation setup, or any normal ExMod migration workflow unless explicitly requested.
- **Do not** optimise for EDS content modelling or document-authoring structure.
- **Do not** infer blocks or page templates unless directly useful for the prototype.
- **Do not** overwrite unrelated project files.
- **Keep changes isolated and reversible.**

---

## Critical Instructions (Internal)

- **This is not a normal migration.** The usual migration instincts are likely wrong.
- **This is** an application UI restyling / reconstruction exercise.
- **The HTML in `html/`** was exported from the real Experience Modernization UI via Chrome “Save page as.” It is not a trustworthy representation of the running UI because iframes and runtime state may be lost in that export.
- **The screenshots** are the only reliable evidence of intended appearance.

### What not to do

- Do not treat the HTML export as a normal webpage to scrape and migrate.
- Do not try to extract a full design system from it and apply a site-wide design migration flow.
- Do not chase semantic fidelity to the exported DOM when it conflicts with what the screenshots clearly show.

### What to do instead

- Reframe the task as: *“Build the closest practical UI prototype from mixed structural and visual evidence.”*
- **Use the MHTML for:** DOM structure, Spectrum class names, `--spectrum-*` design tokens, embedded CSS (ChatPage, ContentPanel, treeBuilders, CodePanel). Extract only shell elements; ignore iframe content.
- **Use the HTML export for:** fallback structure, labels, region ordering, reusable assets.
- **Use screenshots for:** spacing, proportions, alignment, panel boundaries, colour choices, states, visual hierarchy.

---

## Execution Strategy

1. **Identify stable top-level regions** from the screenshots (focus on regions common to both screenshots):
   - **Global header:** hamburger, Adobe AEM logo, Request support, bell, user icon, settings
   - **Left nav sidebar:** dark vertical strip with icons (home, content, folder, code, gear, etc.)
   - **Left panel (Task Progress):** task list, status updates, chat/instruction area, input field
   - **Right panel (Preview):** toolbar (breadcrumbs, document title, Delete, Upload content), document tree (left sub-sidebar), iframe preview area

2. **Treat the preview pane as an empty frame.** Totally ignore its content. Do **not** load any page in it. Do **not** include document view content. Use an empty iframe or a minimal placeholder (e.g. grey box). A previous agent produced `index.html` as a full UPS article; that was wrong.

3. **Reconstruct each region separately** using screenshots for visual fidelity of the **console UI**.

4. **Use critique thinking manually:**
   - Compare implemented output to screenshots
   - List the biggest visual mismatches
   - Fix high-impact discrepancies first

5. **Aim for iterative visual convergence**, not formal migration completeness.

---

## Quality Bar

- Good enough for design review and internal direction.
- Not presented as production-accurate source code for the real app.
- Must clearly distinguish reconstructed UI from real app implementation.

---

## Preferred Output

- **Self-contained prototype** in `html/index.html` that replicates the **ExMod console UI** (shell, panels, toolbars, chat). The preview area should be an empty iframe or minimal placeholder—no page content, no document view content.
- **README update** (`README.md`) explaining:
  - What was derived from HTML
  - What was inferred from screenshots
  - What remains approximate
  - What should be replaced with real app code later.
