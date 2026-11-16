Project card, content only: no fill, border, radius or padding. In `V2 / work-block` each card instance sits in a wrapper board owned by the block (`card` or `outline card`, see the work-block README), which sets the width and the row height. The card fills it; the description fills the free height, so the chips sit at the bottom.

Variants `Type`:
- primary: ink text on the mint `card`. Head: client name (`tag` style, uppercase) then a result headline (Familjen Grotesk 30/1.1 bold, tracking -0.75, `font.size.text-3xl`), 8 apart. Then the title (20/1.25 bold), the description (18/1.625) and up to four `pill` chips (unused ones hidden). Parts 16 apart.
- secondary ("More work"): mint text on the `outline card`. Head: client name then title (24/1.25 bold), 4 apart. Then the description and the chips, with 8px extra space above the chips. Parts 16 apart.

Penpot name `V2 / work-card`, variants `Type` primary, secondary; no `Breakpoint`. In Astro: `WorkCard` with a `type` prop. The previous `work-card` (root, no folder) is V1: `h3-card` title and a `result` line at the bottom. For the wide featured cards see `work-card-featured`.
