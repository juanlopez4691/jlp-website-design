Square buttons (`radius-none`, 0) with a 2px border. Padding 13px 24px, `button` text style.

Penpot variants: `Type` (`primary`, `secondary`, `accent`, `secondary-on-dark`) and `State` (`default`, `hover`, `focus`).

- **Primary**: `ink` fill, `mint` text, ink border. One per block, on light blocks.
- **Secondary**: transparent, ink border and text (`text.on-light`), on light blocks.
- **Accent**: `saffron` fill, ink text, no visible border (the border is the fill color). The primary button on dark blocks (teal, navy, ink).
- **Secondary-on-dark**: transparent, mint border and text, on dark blocks.
- Labels in sentence case: "Tell me about your project", "Email me".

Border rule: a light fill (saffron, mint) gets an ink border only where it would blend into the block behind it, such as primary on hover on the saffron Hero. On a dark block it has no visible border.

States:

| Type              | Hover                                     |
| ----------------- | ----------------------------------------- |
| primary           | `saffron` fill, ink border, ink label     |
| secondary         | `ink` fill, `mint` label                  |
| accent            | `ink` fill, `mint` label                  |
| secondary-on-dark | `mint` fill, no visible border, ink label |

Focus (keyboard only): a 2px gap and then a 2px ring, outside the border. Light-block types (primary, secondary): mint gap, ink ring. Dark-block types (accent, secondary-on-dark): ink gap, saffron ring. In the site use `:hover` and `:focus-visible`, not `:focus`. The ring colors are plain values in Penpot, not tokens.
