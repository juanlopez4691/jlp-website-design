Group of tools on the navy block. Label in uppercase saffron, then chips with a 1.5px mint outline. Core groups (CMS, Backend) invert: saffron fill, navy text, weight 600. Groups sit in auto-fit columns of 320px with a 36px by 40px gap.

In Penpot this is not a component: a component copy cannot change its number of chips, and the groups have 3 to 8. Each group is a plain board named `stack / <name>` (label, then a `chips` row of `pill` copies). In Astro it is one `StackGroup` component that takes a label and a list of chips.
