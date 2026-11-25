# lojopez.dev design system

Source of truth for visuals: the Penpot file. Pages: "00 Foundations"; "01 v1. Components" (the root components, including the blocks that V2 reuses as they are, with an `lg` variant); "02 v1. Home" (the previous Home, for reference); "03 Content"; "04 v2. Components" (the components of the current design, in the asset folder `V2`); "05 v2. Home" (the current Home: boards `Home V2 / xl 1280`, `lg 1024`, `md 768` and `base 390`, each a stack of block instances). V2 is the design to implement. This repo is the written copy of it, kept apart from the code repo (`jlp-website`).

- `tokens.json`: design tokens (colour, type, spacing, radius, layout).
- `penpot-tokens.json`: the same tokens in the format Penpot imports.
- `assets/Figma/tokens-studio.json`: Tokens Studio export.
- `README.md`: content and visual foundations.
- `figma-build-guide.md`: layout of the Home page, block by block (written for Figma, valid for Penpot).
- `components/<Name>/xl.png`, `lg.png`, `md.png`, `base.png`: reference exports of each block from Penpot at 1280, 1024, 768 and 390 wide. Linked from the build issues in `jlp-website`. Re-export them when the layout changes.
- `prototypes/mobile-sliders/`: working HTML prototype of the phone sliders and the experience timeline, and `HANDOVER.md`, the brief to build them.
- `components/<Name>/README.md`: spec per component. `preview.html` is a live example and expects the CSS variables from `tokens.json`.

Keep Penpot and these files in sync by hand when a token changes.
