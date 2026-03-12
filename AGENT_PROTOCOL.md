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

**Provenance:** The `html/` folder content was **exported from the actual Experience Modernization UI** via Chrome’s “Save page as” (or equivalent). That export is the UI we want to style. Chrome export may not preserve iframes, runtime state, or full rendered output—hence the low trust level.

| Source | Role | Trust Level |
|--------|------|-------------|
| **Screenshots** (`screenshots/content-view.png`, `screenshots/page-view.png`) | Visual source of truth | High – use for spacing, proportions, colours, hierarchy, typography |
| **HTML export** (`html/Adobe Experience Manager.html`, `html/Adobe Experience Manager_files/`, etc.) | Partial structural reference; Chrome export of the ExMod UI | Low – may be incomplete or misleading |
| **HTML prototype** (`html/index.html`) | Current implementation | Target of improvement |

**Decision rule:** When HTML and screenshots conflict, **prefer screenshots**.

---

## Goal

Produce a rapid prototype that makes `html/index.html` look and behave as close as practical to the attached target screenshots.

**Focus on:**
- Visible layout, hierarchy, spacing, sizing, typography
- Borders, backgrounds, panel structure
- Interaction affordances (e.g. buttons, links)

**Prioritise:** Practical fidelity over theoretical reconstruction.

---

## Required Workflow

### 1. Analyse

- Analyse the screenshots and HTML export.
- Identify which parts of the UI can be reused from the export and which must be reconstructed from the screenshots.

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
- **Use the HTML export for:** rough DOM structure, labels, region ordering, reusable assets, potential class names.
- **Use screenshots for:** spacing, proportions, alignment, panel boundaries, colour choices, states, visual hierarchy.

---

## Execution Strategy

1. **Identify stable top-level regions** from the screenshots:
   - Header (logo, nav, tools)
   - Breadcrumbs
   - Article header (eyebrow, title, byline, subtitle, hero image)
   - Article body (bullets, paragraphs, subheadings)
   - Social share

2. **Reconstruct each region separately** using screenshots for visual fidelity.

3. **For content outside the main article** (e.g. AEM Task Progress panel, browser chrome, iframe preview): ignore or create a placeholder only if the task explicitly requires it. The primary target is the **article page content** visible in the screenshots.

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

- **Self-contained prototype** in `html/index.html`.
- **README update** (`README.md`) explaining:
  - What was derived from HTML
  - What was inferred from screenshots
  - What remains approximate
  - What should be replaced with real app code later.
