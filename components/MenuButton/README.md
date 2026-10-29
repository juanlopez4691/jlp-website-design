Phone menu button, 24 x 24, at the right of the header, with "EN / ES" on the left. Two states, both built from 2px bars in `text.on-light` (navy):

- `menu-button`: three bars (hamburger), at y 4, 11 and 18. Closed menu.
- `menu-button-close`: two bars rotated 45 and -45 degrees (X). Open menu.

It only exists below `lg` (1024px); from `lg` up the seven nav links show instead. Astro: a `<button>` with `aria-expanded` and an accessible label ("Open menu" / "Close menu"), the bars as one inline SVG that swaps state. The open menu is a full-screen saffron (`surface.hero`) panel: the same header ("EN / ES" on the left, close button on the right), then the seven links in `h3-service` with 24px gaps.
