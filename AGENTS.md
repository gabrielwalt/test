# AEM Experience Modernization Console – Mock

This project is a **standalone HTML mock** of the Adobe Experience Manager (AEM) **Experience Modernization (ExMod) Console** UI.

## What it is

A single-file, fully self-contained prototype that mimics the ExMod console shell:

- **Global header** – Adobe branding, Request support, user avatar
- **Left nav sidebar** – Home, Tasks, Documents, Settings
- **Task Progress panel** – Collapsible task list with progress bar
- **Chat panel** – Messages, input, mode switcher (Plan/Execute)
- **Preview panel** – Toolbar, document tree, view modes, iframe placeholder

The mock uses Adobe Spectrum design tokens (light theme) and is intended for UI prototyping, demos, and design alignment.

## Files

| File | Purpose |
|------|---------|
| `index.html` | Single-file mock: embedded CSS, inline SVGs, no external assets |
| `README.md` | Project overview and usage |

## Usage

Open `index.html` in a browser. No build step or server required.

## Agent instructions

When working on this mock:

- Keep `index.html` fully self-contained (no external CSS, images, or scripts)
- Use Spectrum design tokens (`--spectrum-*`) for consistency
- Preserve the ExMod console structure: header, nav, Task Progress, chat, preview
- The preview iframe should remain empty or a minimal placeholder
