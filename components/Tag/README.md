One component, `pill`, covers every small label. All kinds use `radius-full`. Buttons are not pills: they are square, so the two never look alike.

In Penpot it is a single variant set with two properties: `Kind` (the role) and `Tone` (`on-light` or `on-dark`, the surface it sits on). The coloured tag variants were removed: the client name on a work card is plain uppercase text.

| Kind | Tone | Use |
|---|---|---|
| chip | on-light, on-dark | Technology. `chip` style, 1.5px border in the text color. In the Stack block: `chip-lg`, mint outline; core groups fill with saffron and set weight 600. |
| chip-filled | on-dark | Technology chip with a saffron fill, for core groups on dark blocks. |
| date | on-light | Job period. `date` style, never wraps. |
| fact | on-light, on-dark | `on-light`: 2px navy outline on light blocks. `on-dark`: same shape with a mint outline and mint text, label in saffron, for pills on dark blocks. The hero facts stripe no longer uses pills. Label in `fact-label` plus value at weight 500. |
| availability | on-light | Navy fill, mint text, 10px saffron dot. |

Padding: tags and chips are compact (`space-1` vertical, `space-3` horizontal). Date, fact and availability share a taller size (`space-2` vertical, `space-4` horizontal; the availability pill uses a 10px left padding so the round dot looks aligned).
