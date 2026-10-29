Experience entry drawn as a git log. A 32px graph column on the left holds a 2px navy line and a 14px node (`size.tick`), with a short tick that ends at the date pill. The date pill sits in a 176px column (`size.date-column`), then a 24px gap, then the text. Company goes on its own line under the role title, no bullet.

Variants: `Position` and `Breakpoint` (`xl`, `base`). Position: `first` (saffron node, line only below), `middle` (line through) and `last` (line stops at the node). Stack them with no gap; each row keeps 40px of space at the bottom, except `last`. Newest entry first, so the line reads like `git log`.

`Breakpoint`: `xl` also serves tablet, because the layout is the same and only the width changes. `base` (phones) puts the pill above the title in one column, 12px apart, and the graph stays on the left.

The timeline line is continuous: the first row draws it from the dot down, middle rows draw it over their full height, the last row stops at its dot. Row height follows its content, so the line never breaks.
