Square buttons (`radius-none`, 0) with a 2px border. Padding 13px 24px, `button` text style.

Penpot variants: `Type` (`primary`, `secondary`, `accent`, `secondary-on-dark`) and `State` (`default`, `hover`, `focus`).

- **Primary**: `ink` fill (`surface.ink`), `mint` text. One per block.
- **Secondary**: transparent, ink border and text (`text.on-light`).
- **Accent** (on light blocks): `ink` fill, `mint` text.
- **On dark blocks** (teal, navy, ink): primary becomes `saffron` fill with ink text, secondary becomes `secondary-on-dark`, with mint border and text.
- Labels in sentence case: "Tell me about your project", "Email me".

States:

| Type | Hover |
|---|---|
| primary | `saffron` fill, ink label |
| accent | `ink` fill, `mint` label |
| secondary | `ink` fill, `mint` label |
| secondary-on-dark | `mint` fill, ink label |

Focus (keyboard): two rings outside the button, a 2px gap and then a 2px ring. The ring is ink on light blocks and saffron on dark blocks. In the site use `:hover` and `:focus-visible`, not `:focus`. The ring colors are plain values in Penpot, not tokens.
