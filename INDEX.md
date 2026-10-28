# Design system

Source of truth for visuals: the Penpot file (foundations, components, Home). This folder is the copy the code reads.

- `tokens.json`: design tokens (colour, type, spacing, radius, layout).
- `penpot-tokens.json`: the same tokens in the format Penpot imports.
- `assets/Figma/tokens-studio.json`: Tokens Studio export.
- `README.md`: content and visual foundations.
- `figma-build-guide.md`: layout of the Home page, band by band (written for Figma, valid for Penpot).
- `components/<Name>/README.md`: spec per component. `preview.html` is a live example and expects the CSS variables from `tokens.json`.

Keep Penpot and these files in sync by hand when a token changes.
