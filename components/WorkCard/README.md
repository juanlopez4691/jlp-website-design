V2 project card. Change of rule: unlike V1, the V2 card includes its box, so it is no longer content only. Padding 32 (`space-8`), radius 48 on the top-right and bottom-left corners (`radius-48`). The block sets each card's width and gives the cards in a row the same height. The description fills the free height, so the chips sit at the bottom.

Variants `Type`:
- primary: mint fill (`color.mint`), ink text. Head: client name (`tag` style, uppercase) then a result headline (Familjen Grotesk 30/1.1 bold, tracking -0.75, `font.size.text-3xl`), 8 apart. Then the title (20/1.25 bold), the description (18/1.625) and up to four V1 `pill` chips (unused ones hidden). Parts 16 apart.
- secondary ("More work"): transparent fill, 1.5px mint inner border (`border.thin`), mint text. Head: client name then title (24/1.25 bold), 4 apart. Then the description and the chips, with 8px extra space above the chips. Parts 16 apart.

Penpot name `V2 / work-card`, variants `Type` primary, secondary; no `Breakpoint`. In Astro: `WorkCard` with a `type` prop. V1 (`work-card` in "01 Components": content only, box owned by the block, `radius-lg`, padding 24, `h3-card` title, `result` line) still exists. For the wide featured cards see `work-card-featured`.
