# Figma build guide

Design at 1280px wide, desktop first. Each block is a full-width frame with vertical auto layout; inside it a 1152px container (fixed width, centred, 64px side padding at 1280). Page order: header, hero, facts, What I do, quote, Selected work, Recommendations, How I work, Experience, Stack, Contact, footer.

Section headers (all blocks except hero, facts and quote) are the `section-header` component (1152 wide): eyebrow (`eyebrow`, 21px), then `h2` with no gap between them, 16px before the content, plus 32px of top padding on the content grid. Block vertical padding 80.

## Block structure and surfaces
Every block is the same shell: full-width frame (1280), vertical auto layout, 80px padding top and bottom (`space-20`; the header and facts use 32, the footer 24), one 1152px `container` inside, and the Section arrow as an absolute child. The fill is bound to a `surface.*` token, never a raw colour: `surface.hero` (saffron: header, hero, recommendations), `surface.stack` (navy: facts, stack, footer), `surface.ground` (mint: services, experience), `surface.quote` (coral: quote), `surface.how` (coral: how I work), `surface.work` (teal: work, contact). Each block is a component (see Components below), and a Home board is a stack of block instances. The shell shared by all blocks is not a component of its own, because Penpot has no slots; in Astro it is one `Block` wrapper with a `surface` prop and a slot that each block component uses.

**Layer structure and names.** Top-level boards are named `Home / <breakpoint>`; inside, every block instance is named `block / <name>` (header, hero, facts, services, quote, work, recommendations, how, experience, stack, contact, footer). The `container` holds the content directly (a row or a column), with no extra wrapper of the same size. Grids are named `<content> grid` (`services grid`, `work grid`, `more work grid`, `quotes grid`, `steps grid`, `principles grid`, `stack grid`) and the experience list is `jobs list`. Text layers carry their role (`h1`, `role`, `tagline`, `lead`, `title`, `address`, `note`, `copyright`), arrows are `arrow / from <previous block>`, and background images are named for where they sit (`hero image`, `contact image`). Components are flat kebab-case names (`nav-link`, `nav-lang`, `tick`), with no folders. Tech stack groups are plain boards named `stack / <name>`, not components, because a component copy cannot change its number of chips. Boards that hold a heading with tight leading (h1, h2, mail) do not clip their content, so descenders are never cut; only the blocks clip. Each block has a text label named `label / <component>` outside the boards (left of each Home board, above each variant set on the Components page) so a block can be referenced by name; labels are not part of the design. Hidden layers are only used on purpose: the author photo on tablet and phone, and chips or lines that a given card does not show.

## Components
The Components page has three levels, from small to large (Atomic Design): `Atoms`, `Molecules` and `Blocks`. Each component has its own section with a title, in the order it first appears on Home, and every variant set sits in one container.

- **Atoms** are single elements with no structure of their own: `brand`, `nav-link`, `nav-lang`, `menu-button` (and `menu-button-close`), `button`, `pill`, `eyebrow`, `tick`, `arrow` (the section arrow) and `icon-external-link`.
- **Molecules** are small groups of atoms with one job: `fact`, `section-header`, `service-card`, `work-card`, `quote`, `step`, `principle` and `job-row`. They hold content only. The coloured box around a work card or a quote (fill or border, radius, padding) belongs to the block that uses it, so the same content can be reused on another surface.
- **Blocks** are the organisms, one per block of the page: `header`, `hero-block`, `facts-block`, `services-block`, `quote-block`, `work-block`, `recommendations-block`, `how-block`, `experience-block`, `stack-block`, `contact-block` and `footer`. A Home board is a stack of block instances.

Variant properties follow the design. `Breakpoint` (`xl`, `md`, `base`) exists where the look or the layout changes with the screen: every block, `fact`, `principle`, `job-row` (pill above the text on phones), `section-header` (title size) and `quote` (title size and hidden photo). Components that only change width have no `Breakpoint`: the block sets their width. Colour or kind variants use `Style`, `Tone`, `Type`, `Color` or `Position`: `quote` (`Style` featured or regular), `work-card` (`Style` filled or outline), `section-header` (`Tone` on-light or on-dark), `button`, `pill`, `eyebrow`, `brand`, `service-card` and `job-row`. Variants that only show on a dark surface are repeated in a dark row below the set. Each component maps to one Astro component of the same name in PascalCase (`HeroBlock`, `SectionHeader`, `Quote`), so the Home page is a list of block components. Text overrides on an instance are the page content; structure only changes in the main component.

## Section arrow
A pointed arrow (96 x 40, concave quarter-ellipse sides) hangs from the top edge of a block, centred, in the colour of the block above, so it reads as the previous block pointing into the next. Used on every block that follows a block of a different colour except the facts stripe and the footer. Absolute positioned, so it does not move the content.

## Header (own saffron block, above the hero)
A separate full-width block, not part of the hero. Saffron fill (`surface.hero`), 32px padding top and bottom, nav vertically centred, same 1152px container. Seven nav links (`nav`, 32px gaps) on the left: Services, Work, Recommendations, Process, Experience, Stack, Contact. "EN / ES" on the right.

## Hero (saffron)
Two columns, gap 32, aligned to the top. Left (about 463px wide, 16px gap): availability pill (navy fill, mint text, saffron dot 10px), `h1` "Hi, I'm Joan López" (96px, line height 0.95), `role` "Senior web developer." (24px, 500), a 24px bold tagline (`h3-service` style: "I forge reliable sites with WordPress, WooCommerce, Laravel and Statamic."), `lead` (18px) and two square buttons: "Tell me about your project" (primary navy) and "Download my CV" (outline navy). Right, desktop only: the woodcut, 657x522, transparent PNG or WebP, dark line, never cropped. Block padding: 0 top (the header block above already gives 32 below the nav), 80 bottom (64 on phones). Spacing in the text column (px, below each item): pill 12, `h1` 20, `role` 20, tagline 12, `lead` 16.

## Facts stripe (navy, below the hero)
Full-width navy block (`surface.stack`), padding 32 top and bottom, same container. Five plain columns, each a `tag` label in saffron above a value in `lead` (mint). Tailwind: `grid grid-cols-12 gap-x-8 gap-y-6`, spans 3, 2, 2, 2, 3 (Core stack, Experience, Clients, Based in, Languages; ordered by relevance to a client).

## What I do (mint block)
Eyebrow "What I do", `h2` "Where I can help", then six service cards in two rows of three, gap 24 (3 columns of 368). Card: padding 32, height of the tallest card in the row, vertical gap 16, `radius-48` (48) on the top-right and bottom-left corners only. Titles are one line each (`h3-service`): WordPress, Laravel and Statamic, Migrations, Performance, APIs and integrations, Maintenance and support. Fills in a diagonal rotation so equal colours never touch: saffron, coral, teal / teal, saffron, coral. Text navy; mint on teal.

## Quote (coral block)
One quote taken from a recommendation: `quote-big` (36, weight 300), navy, max 896px wide, with two large decorative quotation marks behind it (SVG icon `assets/icons/quote-mark.svg`, 288 wide, mint at 30% opacity: opening at the top left, the same mark rotated 180 degrees at the bottom right, cropped by the block edge) and the author underneath (name 18 regular, role 16, 16px gap). The text block is centred in the container. Padding 80 top and bottom.

## Selected work (teal block)
Eyebrow "Selected work", `h2` "Things I've built", then two columns of work cards, gap 24, three rows (each row takes the tallest card). Card: mint fill, 8px radius, padding 24, gap 16. Contents in order: client name (`tag`, uppercase, plain text), `h3-card`, `body`, `result` line, chips (pills). Chips stay at the bottom. Then `sub` "More work" and three outline cards (1.5px mint border, transparent, mint text), same padding.

## Recommendations (saffron block)
Eyebrow, `h2` "What people say about me". Featured quote: navy fill, mint text, `quote-big`, `radius-28`, padding 48. Under it four white cards (two columns, gap 24, `radius-28`, padding 32): quote first, then the author pinned to the bottom (50px round photo centred vertically against the name and role, name `lead` at weight 600 with the 12px `icon-external-link` linking to LinkedIn, role `body`, 8px between photo and text). Bottom right: link "Read them all on LinkedIn" with the same icon (`button` weight 600, navy).

## How I work (coral block)
Eyebrow "Process", `h2` "How I work". First, four numbered steps in a row (gap 40, 258px each): 2px navy rule, title "1. Listen and learn", "2. Plan and propose", "3. Build and verify", "4. Launch and support" in `h3-card` (24), then `body`. Then, 64px below, four principles in two columns (gap 40): title `h3-service` (24) and a paragraph. Principles: I own the technical side end to end; I build for real use; Tests and static analysis in the pipeline; AI is part of my daily workflow.

## Experience (mint block)
Eyebrow "Experience", `h2` "25+ years building for the web". Rows drawn as a git log (see Job row): continuous 2px line, nodes and ticks aligned to the date pill centre, date column 176px.

## Stack (navy block)
Eyebrow "Tech stack" in saffron, `h2` "Tools I work with", auto-fit columns of 320px, gap 40 both ways. Group label: `label` saffron. Chips: 1.5px mint outline, `pill`. Core groups (CMS, Backend): saffron fill, navy text, weight 600.

## Contact (teal block)
Eyebrow, then "Let's talk about what you're building." and the address in `mail` (Figtree 400) saffron, two buttons (Email me: saffron fill; LinkedIn: mint outline), one line of text below. Background (desktop and tablet): low-contrast engraving, dark line on transparent, behind the text, anchored to the right edge of the block; hidden on phones.

## Footer (navy)
One row, space-between, padding 24 top and bottom, three parts: Download my CV and GitHub on the left, Legal notice, Privacy and Cookies in the middle, the copyright on the right. Items in a group are separated by a bullet (`•`) with 12px on each side.

## Phone (390px, `base`)
Same blocks in the same order, one column, built on `Home / base 390`. Side padding 32 (container 326), block vertical padding 64 (`space-16`), same `surface.*` fills, arrow centred (96 x 40 stays). Only the Display styles shrink (see "Display mobile" in `tokens.json`; tokens `font.size.*-base` and `font.tracking.*-base`): h1 48, h2 36, mail 30, quote-big 24; every other style keeps its desktop size.

- **Header:** "EN / ES" (`nav`) on the left, `menu-button` on the right, no nav links and no brand name (the name is in the hero title). The open menu is a second frame (`Menu / base 390 (open)`): saffron panel, same header with `menu-button-close` on the right, then the seven links in `h3-service` (24 gap).
- **Hero:** no woodcut. Availability pill on one line with shorter copy, "Open to freelance and full-time work" (the full text wraps on 390; keep it as a separate short string for i18n), h1, role, tagline, lead, then the two buttons stacked at full width (gap 16, label centred).
- **Facts:** Core stack full width, then two columns of 151 (Experience and Clients, Based in and Languages), gap 24 both ways (flex row wrap). Items have auto height, never a fixed one.
- **Cards:** services, work, "More work" and recommendations in a single column at full width, gap 24, card padding 24 on recommendation cards (no author photo); cards grow to fit their text. Chips wrap.
- **Quote block:** decorative marks 128 wide in the corners, text left-aligned; author and role on separate lines (no leading dot).
- **How I work:** four steps stacked (gap 32), then the four principles stacked (gap 24).
- **Experience:** the git log line stays on the left (32 wide); the date pill sits above the title and text. Each row is as tall as its content, so spine and tick follow it.
- **Stack:** groups stacked, chips wrap.
- **Contact:** title (h2 mobile) and address (mail mobile) stacked, buttons stacked at full width, text below. No background engraving on phones.
- **Footer:** three rows: copyright, then Download my CV and GitHub, then Legal notice, Privacy and Cookies; each row wraps if needed.

## Tablet (768px, `md`)
Same blocks in the same order, built on `Home / md 768` (open menu: `Menu / md 768 (open)`). Side padding 32 (container 704), block padding 80, same `surface.*` fills, arrow centred. Display styles use `Display tablet` (tokens `font.size.*-md` and `font.tracking.*-md`: h1 60, h2 48, mail 48, quote-big 30); everything else keeps its desktop size.

- **Header:** same as phone: "EN / ES" left, `menu-button` right; the seven links only appear from `xl` (1280px).
- **Hero:** no woodcut (as on phone). One text column 560 wide, centred in the container, with 24 between the text block and the buttons, which sit side by side (gap 16).
- **Facts:** two columns of 340 (gap 24), in reading order: Core stack, Experience and Clients in the first column, Based in and Languages in the second. In Penpot the container is a row with two `column` boards (vertical flex, gap 24); in Tailwind `grid grid-cols-2 gap-6` with two `flex flex-col gap-6` stacks. Items have auto height, never a fixed one.
- **Cards:** two columns of 340 (gap 24) for services (rows 206, 206 and 188 high), work, "More work" (2 + 1) and recommendations. Cards in a row share the height of the tallest, and the author line stays pinned to the bottom of recommendation cards. No author photo on tablet.
- **Quote block:** decorative marks 192 wide in the corners, 40px from the side (same as desktop), text 30 light.
- **How I work:** the four steps in a 2 x 2 grid (336 each, gap 32), the four principles in two columns.
- **Experience:** git log as on desktop with the 176px date column, text column 432.
- **Stack:** two columns of 340.
- **Contact:** title (h2 tablet) and address (mail tablet) stacked, buttons side by side. The background engraving keeps its desktop position, anchored to the right edge of the block.
- **Footer:** one row as on desktop: Download my CV and GitHub, legal links, copyright.
