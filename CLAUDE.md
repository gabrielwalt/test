# Claude Code Instructions

**Primary instructions for Claude Code working on this project.** Full protocol: [AGENT_PROTOCOL.md](./AGENT_PROTOCOL.md).

---

## Source Provenance

The `html/` folder contains what was **exported from the actual Experience Modernization UI** using Chrome’s “Save page as” (or equivalent). That export is the UI we want to restyle. It may be incomplete or misleading because Chrome export does not reliably capture iframes, runtime state, or the full rendered output.

---

## Essential Rules

1. **Screenshots are source of truth.** `screenshots/content-view.png` and `screenshots/page-view.png` define the target appearance.
2. **HTML export is partial reference only.** The Chrome export in `html/` (e.g. `Adobe Experience Manager.html`, `Adobe Experience Manager_files/`) provides structure, labels, assets—not authoritative layout or styling.
3. **When HTML and screenshots conflict, prefer screenshots.**

---

## Task

Make `html/index.html` look and behave as close as practical to the screenshots. This is **UI prototyping**, not website migration.

---

## Workflow

1. **Analyse** screenshots and HTML export.
2. **Plan** before changing anything (assumptions, missing info, approximations).
3. **Implement** in the simplest maintainable way.
4. **Critique** against screenshots and refine.

---

## Do Not

- Run migration, import, or design-migration workflows.
- Optimise for EDS, CMS, or content modelling.
- Overwrite unrelated files.

---

## Do

- Use HTML export for: DOM structure, labels, region order, class names.
- Use screenshots for: spacing, typography, colours, hierarchy, alignment.
- Keep changes isolated and reversible.
- Update README provenance table after implementation.

---

## Reference Files

| File | Purpose |
|------|---------|
| [AGENT_PROTOCOL.md](./AGENT_PROTOCOL.md) | Full workflow, constraints, execution strategy |
| [README.md](./README.md) | Project overview, provenance table |
