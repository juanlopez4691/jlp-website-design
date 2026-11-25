# Handover: phone sliders and experience timeline on the Home page

For the Senior Dev planning agent of `jlp-website`. This is a brief, not a spec: write `spec.md` from it. Paths under `src/` are in `jlp-website`, the rest are in this repo. The code was read at `f63bf46` (`main`).

## Goal

Below `md` (768), show services, the non-featured work cards and the regular recommendations as swipeable sliders, and experience as a horizontal timeline. The Home at 390 goes from 16346 to 11135px tall in Penpot. Nothing changes from `md` up in the code.

## Sources, in order of authority

1. Joan's decisions, below.
2. Penpot, page "05 v2. Home", board `Home V2 / base 390`. Components on "04 v2. Components": `V2 / services-block`, `V2 / work-block`, `V2 / recommendations-block`, `V2 / experience-block` (variant base), `V2 / job-row` and `V2 / slider-dots`.
3. `components/SliderDots/README.md` (dots and shared behaviour), and the READMEs of `ServicesBlock`, `WorkBlock`, `RecommendationsBlock`, `ExperienceBlock`, `JobRow` and `Quote`. Images: `base.png` of the four blocks.
4. `prototypes/mobile-sliders/index.html`: reference for behaviour and for 391 to 767, where Penpot has no frame. Run `python3 -m http.server 8390` from this repo and open `/prototypes/mobile-sliders/`. The defaults of its control panel are the approved design; the other options were rejected. It is not code to copy (see "Do not copy").

## Decisions made by Joan

| Topic | Decision |
|---|---|
| Services | Slider of 2 rows by 3 columns. Two columns in view from 620 |
| Selected work | The two featured cards stay stacked, full width. The four primary cards are a slider |
| More work | Its own, independent slider |
| Recommendations | The featured card stays above. The four regular ones are a slider |
| Work and recommendations sliders | Two cards in view from 680 |
| Navigation | Dots only. No arrows, no counter |
| Card width | Same for all cards, original paddings. One in view is the container width |
| Column gap | 20 (services rows stay 24) |
| Snap (cards) | Center (left edge where two are in view) |
| Card height | Equal within a slider |
| Long quotes | "Read more", cut at the end of the first paragraph, never mid-sentence |
| Experience | Horizontal timeline, newest first. Jobs 90% of the container with one in view, two in view from 680 |
| Timeline drawing | Line with nodes. Node and connector centered over the date pill |
| Timeline snap | Left, at every width |
| Author photos | Shown at every breakpoint, as the site already does. Only the design was out of date |
| Toggle copy | "Read more" / "Read less", "Leer más" / "Leer menos" |
| Dot label | "Go to position 2 of 4" / "Ir a la posición 2 de 4" |
| Slider label | The title already on the page. No new copy |
| Versioning | Stays in V2 |

Why the paragraph rule matters: a cut by lines left "His huge..." hanging in Julià's quote. Do not use `line-clamp`.

## Values

| | up to 619 | 620 to 679 | 680 to 767 | from 768 |
|---|---|---|---|---|
| Services columns in view | 1 | 2 | 2 | grid, as now |
| Other cards in view | 1 | 1 | 2 | grid, as now |
| Jobs in view | 1 (90%) | 1 (90%) | 2 | log, as now |
| Dots: experience | 5 | 5 | 4 | none |
| Dots: services | 3 | 2 | 2 | none |
| Dots: selected / more / recommendations | 4 / 3 / 4 | 4 / 3 / 4 | 3 / 2 / 3 | none |

Track: `-mx-8 px-8 scroll-px-8`, `gap-x-5`, hidden scrollbar, `snap-x snap-mandatory`, items `snap-always`, contained horizontal overscroll. Card: 100% of the container, or `(100% - 1.25rem) / 2`. Dots: 16 below the track; 12px circle, 2px outline, 24 x 44 hit area.
Timeline: 30px graph over the date pill; 2px line centred 7px from the top, 14px node, 1.5px connector of 16px. Job: 90% of the container, or `(100% - 1.25rem) / 2`. Text styles do not change.
Toggle: 16px, weight 500, underlined, 8px above, 4px vertical padding. Card padding, radius, fills and type do not change.

Reference heights at 390 in Penpot: services 756, work 2480, recommendations 1322, experience 635. The browser prototype measured 748, 2472, 1309 (before the photos were added) and 635. Do not assert exact heights.

## Where it lands in the code

| File | Change |
|---|---|
| `src/components/blocks/ServicesBlock.astro` | The `ul` becomes a two-row slider below `md` |
| `src/components/blocks/WorkBlock.astro` | `work.items` and `work.more` become sliders. `work.featured` does not change |
| `src/components/blocks/RecommendationsBlock.astro` | `rest` becomes a slider. Featured card and link do not change |
| `src/components/blocks/ExperienceBlock.astro`, `src/components/molecules/JobRow.astro` | The `ol` becomes the timeline below `md`. The log from `md` up does not change |
| `src/components/molecules/Quote.astro` | "Read more" for regular quotes with more than one paragraph |
| New slider component | Wraps the list, owns the dots and the script. Used five times, on a `ul` or an `ol` |
| `src/i18n/` or the block schemas in `src/libs/blocks/` | The new labels, in both languages |

`quote` is already an array of paragraphs in `src/content/home/{en,es}.yaml`, so the cut needs no content change. Today only Julià's has two.

## Risks to solve in the spec

1. **Reveal animations.** The list items use `motion-safe:scroll-triggered:reveal`, whose `view()` timeline follows the nearest scroll container. A slider is one: `overflow-x: auto` also computes `overflow-y` to `auto`. Items may never trigger and stay at opacity 0. Likely answer: below `md`, reveal the slider as a whole and not its items; keep the per-item reveal and the `reveal-stagger-*` from `md`. Read from the code and the CSS model, not tested: check it in a Chrome with triggers.
2. **Vertical clipping.** The same `overflow-y` clips focus outlines and any lift. It affects open issue #100 (lift work cards on hover). Leave room with padding and a matching negative margin.
3. **Breakpoints.** `AGENTS.md` allows only base, `md`, `lg` and `xl`, with one exception for `sm`. 620 and 680 need a second one: arbitrary variants (`min-[620px]:`, `min-[680px]:`), bounded below `md`. Put it under "Proposed rule changes" in the PR.
4. **CSP.** No inline `style` attributes or `<style>`. A bundled `<script>` in the component works, as in `HowBlock.astro`. Pass column counts with classes.
5. **Two-row services.** The list order must stay as it is. Filling by rows with three columns gives the right pairs: WordPress over Performance, Laravel over APIs, Migrations over Maintenance. Filling by columns puts two teal cards together.
6. **Dots are stops, not cards.** Recompute on resize, clamp each stop to the maximum scroll and merge equal ones. Hide the row when there is one stop, and always from `md`.
7. **No JavaScript.** The sliders must still swipe, with the dots hidden (they need the script). The full quotes must be readable: collapse only when the script runs, without layout shift if possible.
8. **Crossing `md`.** Resizing or rotating past 768 must restore the grid and the full quotes, whatever the state.
9. **Print.** A printed page must not lose the cards that are out of view.
10. **One `JobRow`, two layouts.** Today it uses `subgrid` inside the `ol` grid (`grid-cols-[auto_1fr] pl-8`), which only works with the log. Below `md` each `li` is a stop with its own head. Keep one markup for both and no duplicated text.
11. **Timeline line.** Segments must not depend on the pill width, which changes per language. The prototype draws the left and right half of the pill plus a rail up to the next job, with 1px overlaps that hide seams. The line must not widen the scroll area past the last node.
12. **Snap differs.** Cards center, the timeline snaps left, so the stop calculation needs the mode. The last job cannot reach the left edge at 90%: its stop is the maximum scroll.
13. **Opening "Read more"** makes that slider taller, because its cards share one height. That is accepted.

## Accessibility

- Keep `ul` / `li` semantics. Each slider is a labelled region around its list, and the scroller takes keyboard focus below `md` only.
- Dots are buttons with a translated label and `aria-current`. "Read more" is a button with `aria-expanded`.
- Focus outlines follow the rules in `AGENTS.md`: ink on light blocks, saffron on dark ones. Dots must stay visible in forced-colors mode.
- Reduced motion: jump, no smooth scroll.
- Cards out of view keep their links reachable by keyboard; focusing one scrolls it into view.

## Do not copy from the prototype

- `role="group"` on the `ul`: it removes the list semantics.
- Content in JavaScript, `innerHTML` rendering, custom properties set from script, the Google Fonts link (the CSP blocks it), and the static images.
- Links, which are inert there.

## Suggested split

1. `feat`: slider component with dots, used in services.
2. `feat`: sliders in work.
3. `feat`: slider in recommendations.
4. `feat`: experience timeline.
5. `feat`: "Read more" in the quote.

2, 3 and 4 depend on 1 through the component. 5 does not depend on it.

## Acceptance criteria

Check in English and Spanish, at 360, 390, 430, 619, 620, 679, 680, 767 and 768.

- [ ] `lint`, `format:check`, `check`, `test` and `build` pass.
- [ ] Columns in view and dots match the table under "Values", on both sides of each break.
- [ ] From 768 up the page looks the same as before.
- [ ] Below 768 the page itself never scrolls sideways.
- [ ] One card in view: featured and slider cards have the same width. The gap is 20 and the cards of a slider share one height, with pills and author at the bottom.
- [ ] Swiping, the dots and the keyboard reach every card, and the current dot is right, including on the last card.
- [ ] No two teal service cards touch in the two-row slider.
- [ ] Julià's quote stops at the end of its first paragraph in both languages ("media publishers..." / "medios de comunicación..."). The toggle opens and closes it. From 768 the full text shows, with no toggle.
- [ ] In the timeline the node and connector are centered over every date pill in both languages, and the line has no gaps from the first node to the last, with none beyond it.
- [ ] The first four jobs rest on the left edge of the container with one in view. The last one ends at the right edge.
- [ ] Author photos show at every width, as before.
- [ ] Every card is visible after scrolling with scroll triggers supported, not supported, and with reduced motion.
- [ ] With JavaScript off, all text and all cards are reachable.
- [ ] No CSP errors in the console.
- [ ] Swiped on a real iOS Safari and a real Android Chrome.

The stop calculation (clamp, merge, current index) is worth a `*.test.ts` in `src/libs/`.

## Open questions for Joan

None. Joan answered the copy, label and photo questions (see "Decisions").

Optional cleanup in `Quote.astro`: the comment "hidden below lg" and the `lg:block` class are leftovers.

## Known gaps outside this work

- Penpot `service-card` has a gap of 12 at 390; its README and the site say 16. Keep 16.

## Not in this work

Changes to other blocks, to the card designs or to any layout from `md` up. Autoplay, looping, arrows or a carousel library.
