Square buttons (`radius-none`, 0) with a 2px border. Padding 13px 24px, `button` text style.

Penpot variants: `Type` (`primary`, `secondary`, `primary-on-dark`, `secondary-on-dark`) and `State` (`default`, `hover`, `focus`).

| Type | Where | Default | Hover |
|---|---|---|---|
| primary | light blocks, one per block | `ink` fill and border, `mint` text | `saffron` fill, `ink` text, ink border |
| secondary | light blocks | transparent, `ink` border and text | `ink` fill, `mint` text |
| primary-on-dark | dark blocks | `saffron` fill and border, `ink` text | `ink` fill and border, `mint` text |
| secondary-on-dark | dark blocks | transparent, `mint` border and text | `mint` fill, `ink` text |

Border rule: a light fill (saffron, mint) gets an ink border only where it would blend into the block behind it. On a dark block it has none, so `primary-on-dark` has a saffron border, not an ink one. The hover of `primary` keeps its ink border because the saffron fill would blend into a saffron block.

Focus (keyboard only): two rings outside the border, a 2px gap and then a 2px ring.

| Type | Gap | Ring |
|---|---|---|
| primary, secondary | `mint` | `ink` |
| primary-on-dark, secondary-on-dark | `ink` | `saffron` |

In the site use `:focus-visible`, not `:focus`, and no `box-shadow`, so the focus stays visible in forced-colors mode. The gap and ring colors are plain values in Penpot, not tokens. Labels in sentence case: "Tell me about your project", "Email me".
