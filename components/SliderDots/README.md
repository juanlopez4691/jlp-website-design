Navigation of the phone sliders (services, selected work, more work, recommendations) and of the experience timeline. A centered row of dots, one per stop, below the slider. Only below `md`.

- Dot: 12px circle, 2px outline (`border.regular`), `radius-full`. The current one is filled.
- Hit area: 24 x 44 per dot, no gap between them, so the row is 72 wide (3 dots), 96 (4) or 120 (5) and 44 tall.
- Colour: the block's text token, `text.on-light` (services, recommendations, experience) or `text.on-dark` (work).
- One dot per stop, not per card: cards that end up at the same scroll position share a dot. With one stop there are no dots.
- Each dot is a button labelled "Go to position 2 of 4" / "Ir a la posición 2 de 4", with `aria-current` on the current one. Each slider is labelled with the title already on the page ("How I can help", "Things I've built", "More work", "What people say about me", "25+ years building for the web").

Penpot name `V2 / slider-dots`, variants `Tone` on-light or on-dark and `Count` 3, 4 or 5 (5 only on-light).

Space above the row: 16px (Penpot and prototype). The 12px circle sits centered in the 44px row.

## Slider behaviour

Shared by the four blocks, below `md` (768). From `md` up the blocks are the grids they were.

- Native horizontal scroll with scroll snap (`mandatory`, always stop). Cards snap centered while one is in view, to the left edge while two are. The experience timeline always snaps left, and its jobs are 90% of the container while one is in view. For the cards, at these widths, both place the card on the container's left edge.
- The track bleeds to both screen edges and its first card starts at the container (32px). Gap between columns 20 (`space-5`).
- One card in view: the card is as wide as the container, 326 at 390, so 12px of the next one shows. Two in view: `(container - 20) / 2`.
- Breaks: services shows two columns from 620, the other sliders two cards from 680.
- All cards of a slider share the height of the tallest (experience jobs have no card, so they do not stretch). The last part stays pinned to the bottom.
- No scrollbar. Prefers-reduced-motion: a dot jumps instead of scrolling.

| Screen | Services | Selected work, More work, Recommendations | Experience |
|---|---|---|---|
| up to 619 | 1 column, 3 dots | 1 card, 4 / 3 / 4 dots | 1 job, 5 dots |
| 620 to 679 | 2 columns, 2 dots | 1 card, 4 / 3 / 4 dots | 1 job, 5 dots |
| 680 to 767 | 2 columns, 2 dots | 2 cards, 3 / 2 / 3 dots | 2 jobs, 4 dots |

There is no Penpot frame between 390 and 768. The prototype in `prototypes/mobile-sliders/` is the reference for that range.
