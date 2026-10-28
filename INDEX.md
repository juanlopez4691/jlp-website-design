# lojopez.dev design system

Source of truth for visuals: the Penpot file (foundations, components, Home). This repo is the written copy of it, kept apart from the code repo (`jlp-website`).

- `tokens.json`: design tokens (colour, type, spacing, radius, layout).
- `penpot-tokens.json`: the same tokens in the format Penpot imports.
- `assets/Figma/tokens-studio.json`: Tokens Studio export.
- `README.md`: content and visual foundations.
- `figma-build-guide.md`: layout of the Home page, band by band (written for Figma, valid for Penpot).
- `components/<Name>/README.md`: spec per component. `preview.html` is a live example and expects the CSS variables from `tokens.json`.

Keep Penpot and these files in sync by hand when a token changes.
