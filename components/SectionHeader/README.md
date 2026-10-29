Header that opens every block except the hero, facts, quote and contact: the eyebrow (`tag` style, uppercase) stacked directly over the title (`h2`, 60/1/-1.5), no gap between them, 1152 wide (the container). Used by services, work, recommendations, how I work, experience and stack. Contact only uses the eyebrow, because its title is the big mail line.

Colours: both texts use the block's text token, `text.on-light` (navy) on light blocks and `text.on-dark` (mint) on dark ones (work, stack). The eyebrow and the title never repeat the same words. The 16 px between the header and the content comes from the block's gap, not from the component.

Variants: `Breakpoint` xl, md, base (the title steps down from 60 to 48 and 36, with the matching tracking) and `Tone` on-light or on-dark (title and eyebrow colours). Penpot: component `section-header` (nested `eyebrow` instance plus the title text). Astro: `<SectionHeader eyebrow="..." title="..." />`, text colour inherited from the block.
