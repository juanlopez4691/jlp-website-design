Experience entry drawn as a git log. A 32px graph column on the left holds a 2px ink line and a 14px node (`size.tick`), with a short tick that ends at the date pill. The date pill sits in a 176px column (`size.date-column`), then a 24px gap, then the text. Company goes on its own line under the role title (16px, line height 1.25), no bullet. The description is in `body-lg` (18px, line height 1.5).

Variants: `Position` and `Breakpoint` (`xl`, `base`). Position: `first` (saffron node, line only below), `middle` (line through) and `last` (line stops at the node). Stack them with no gap; each row keeps 40px of space at the bottom, except `last`. Newest entry first, so the line reads like `git log`.

`Breakpoint`: `xl` also serves tablet, because the layout is the same and only the width changes. `base` is V1 only: below `md` the current design uses `V2 / job-row`.

The timeline line is continuous: the first row draws it from the dot down, middle rows draw it over their full height, the last row stops at its dot. Row height follows its content, so the line never breaks.

## Below `md`: `V2 / job-row`

A stop of the horizontal timeline. Same text styles as above, in one column: graph, date pill, 12px, then the text.

- Graph: 30px tall, over the pill. A 2px ink line with its centre 7px from the top, the 14px node on it, and a 1.5px connector from the node to the pill (16px).
- Node and connector are centered over the date pill, whatever its width. The pill is as wide as its text plus padding and starts at the left edge of the job.
- The line is continuous across the 32px gaps: each rail reaches into the gap up to the next job. It starts at the first node and stops at the last one.
- The newest job comes first and its node is saffron; the others are ink.
- Jobs have no box. Their height follows the content, top-aligned.

Penpot name `V2 / job-row`, variants `Position` first, middle, last.
