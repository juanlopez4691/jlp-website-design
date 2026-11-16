Wide work card for `V2 / work-block`: a result panel and a body panel, content only. The block wraps each instance in a `featured card` board (mint fill, `radius-48` on the top-right and bottom-left corners, clips its content, no padding), which sets the width and the row height; the two panels keep their own 32 padding.

- Result panel: fill `color.saffron` or `color.coral` (part of the card content), padding 32. Client name (`tag`, uppercase), then the result (Familjen Grotesk bold, line height 1): 48px (`font.size.text-5xl`) in the row layouts, 36px (`font.size.text-4xl`) stacked.
- Body panel: padding 32. Title (24/1.25 bold) and description (18/1.625), then the chips at the bottom (`pill`). Gap 24 in the row layouts, 16 stacked.

Variants: `Layout` row (result left, columns 5fr / 7fr), row-reversed (body left, 7fr / 5fr), stacked (result on top); `Color` saffron, coral. The card fills the height of its wrapper; the taller panel decides it (277 and 229 at xl, 277 and 257 at lg); stacked hugs its content. The block picks the layout by breakpoint: row and row-reversed at xl and lg, stacked at md and base. Penpot name `V2 / work-card-featured`.
