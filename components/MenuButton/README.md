Phone menu button, 44 x 44 (the touch target), at the right of the header, with "EN / ES" on the left. Two states, both built from 24 x 2px bars in `text.on-light` (navy), centred in the 44px box (Astro: `size-11` with `-m-2.5`, so the header keeps its 32px padding and its 88px height):

- `menu-button`: three bars (hamburger), at y 14, 21 and 28. Closed menu.
- `menu-button-close`: two bars rotated 45 and -45 degrees (X). Open menu.

It only exists below `xl` (1280px); from `xl` up the eight nav links show instead. Astro: a `<button>` with `aria-expanded` and an accessible label ("Open menu" / "Close menu"), the bars as one inline SVG that swaps state. The open menu is a full-screen saffron (`surface.hero`) panel: the same header ("EN / ES" on the left, close button on the right), then the eight links in `h3-service` with 24px gaps.
