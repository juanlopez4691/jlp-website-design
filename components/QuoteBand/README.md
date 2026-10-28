Full-width coral band (`surface.quote`) that holds one short quote taken from a recommendation. Made of: the section arrow (mint, centred on the top edge), a container (1152px) with the curly quotation mark on the left (Playfair Display, 128px, `text.on-dark`) and the text column next to it, 32px apart. The text column has the quote in `quote-big` (max 896px wide, `text.on-light`) and, 16px below, the author line: name in `lead`, then the role in `body-sm`, 8px apart. The whole block is centred. Padding 80 top and bottom.

Content rules: the quote is a sentence or two from a real recommendation, in the person's own words, without ellipsis tricks. The author is always named. To reuse the band, change the quote, name and role, and override the arrow colour to the colour of the band above.

In Penpot the main component `quote-band` lives on the Components page and contains an instance of `arrow`.
