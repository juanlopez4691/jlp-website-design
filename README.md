# lojopez.dev

Color blocks: a bright, flat system for the portfolio of Joan López, a senior full stack developer. Full-width blocks in saffron, coral, teal and navy, pill-shaped labels, square buttons and one woodcut engraving of a blacksmith.

## Content fundamentals

- First person, direct. "Hi, I'm Joan López." "I take care of the technical side, from architecture to launch, so your project works on day one and stays fast, secure and easy to maintain."
- Short sentences with concrete nouns: Statamic, WooCommerce, Laravel, TicketBAI. No sales language, no superlatives.
- No em dashes or en dashes. Dates read "Jan 2021 to Present".
- Sentence case for titles and buttons: "Get in touch", "Email me". Uppercase only for eyebrows, client tags and fact labels.
- Each work card states what was built, then one line of result in `result` weight.
- Every section has an eyebrow plus a title, and the two never repeat the same words: "What I do" / "Where I can help", "Selected work" / "Things I've built", "Process" / "How I work", "Experience" / "25+ years building for the web".
- Quotes on the page are fragments taken from real recommendations, with the author named.

## Visual foundations

**Color.** Mint is the ground. Each block takes one color: saffron (hero and recommendations), mint (services and experience), teal (work and contact), coral (quote and how I work), navy (facts, stack and footer). Text on saffron, coral and mint is `navy`. Text on teal and navy is `mint`. `saffron` is also the accent on navy and teal: core chips, the availability dot, the contact address, the stack labels.

**Shape.** Small labels are pills (`radius-full`): chips, fact pills, date pills. The client name on a work card is plain uppercase text in the `tag` style, not a pill. Buttons are square (`radius-none`, 0) so they never read as labels. Service cards round two opposite corners (`radius-48`, 48px, top right and bottom left). Each block after a block of a different colour starts with a pointed arrow in the previous block's colour (the Section arrow), so one block points into the next. Work cards are nearly square (`radius-lg`). All recommendation cards, featured or regular, share one radius (`radius-28`, 28px). Radius token names follow Tailwind: `radius-lg` is `rounded-lg`, `radius-full` is `rounded-full`, `radius-none` is `rounded-none`. The two values Tailwind has no class for are written as `rounded-[28px]` (`radius-28`) and `rounded-[48px]` (`radius-48`).

**Type.** Familjen Grotesk (700, tight tracking) for display and titles. Figtree for text, labels and buttons, for the contact address at weight 400 (`mail`) and for the featured quote at weight 300 (`quote-big`). Both from Google Fonts. Sizes are Tailwind defaults: h1 `text-8xl` (96px, line height 0.95), h2 `text-6xl` (60px), role and card titles `text-2xl` (24px), hero lead `text-lg` (18px). Titles tighten as they grow: h1 -2.4px tracking, h2 -1.5px.

**Long-form pages.** Blog, case studies and legal pages use the `Content` styles: h1 to h6 in Familjen Grotesk 700, body in Figtree 18px with line height 1.625, a 65ch reading column, and the prose rules in `tokens.json`. Everything maps to default Tailwind classes (`text-lg leading-relaxed`, `max-w-prose`, `space-y-6`). Sizes step at `md` (768px) instead of scaling fluidly, so Tailwind needs no custom values. Only the Display styles shrink (each size has a `font.size.*` and `font.tracking.*` token per breakpoint, bound to the text in Penpot): `Display tablet` at md (h1 60, h2 48, mail 48, quote-big 30) and `Display mobile` below it (h1 48, h2 36, mail 30, quote-big 24).

**Layout.** One container (`container`, 1152px) inside full-bleed blocks. Blocks use `space-20` vertical padding. Cards sit in auto-fit grids with a `space-5` gap. Hero: nav left and language switch right, then text left and engraving right on desktop (tablet and phone have no hero image; the image is as tall as the text block and is never cropped; transparent woodcut, navy ink). Under the hero, a full-width navy stripe holds the key facts as five plain label and value columns (no pills), inside the same 1152px container. Cards in one row share the height of the tallest card (service cards are a fixed 182px); client name and tags, or the author and avatar, stay pinned to the bottom.

**Imagery.** One engraving only: a 16th-century woodcut of a blacksmith at the anvil, dark line on transparent, never inverted. It appears twice: in the hero (desktop only) and, faint, behind the contact text (desktop and tablet; hidden on phones). Wellcome Collection, public domain; confirm the licence in the Commons record before publishing.

**No** gradients, shadows, icons or emoji. Depth comes from color fields and borders (`2px` navy outlines, `1.5px` mint on dark blocks).

## Iconography

One exception: a small external-link icon, `icon-external-link` (12px, 1.5px stroke, same color as the text, 8px gap) after the author name in recommendation cards, to show that the name links to their LinkedIn profile. No other icons. The pill label does the job of an icon elsewhere.

## Using this in Figma

1. Install the Tokens Studio for Figma plugin. Load `assets/Figma/tokens-studio.json` (Settings, Add new, JSON). Create styles for colors and text, and variables for spacing and radius.
2. Install the fonts Familjen Grotesk (500, 600, 700) and Figtree (300, 400, 500, 600) from Google Fonts.
3. Build the page at 1280px wide with the layout in the "Figma build guide" section: auto layout everywhere, container 1152px, blocks as full-width frames.
4. Components to create first: Button (primary, secondary, accent, secondary-on-dark), Pill (chip, date, fact, availability), Section arrow, Section header, Menu button, Step, Quote block, Service card, Work card, Job row, Quote. Each has a live preview and a spec in this system.
