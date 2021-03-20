# Units

## Pixels

- Correspond more or less with what you see on screen

## Ems

- A relative unit, equal to the font size of the current element

- I.e. if a heading has a font size of 24px and its given a bottom padding of 2em, the padding will be 48px

## Rems

- Similar to em but it's always relative to the root element, the `html` tag

- This means that, as a default `html` tag has a font size of 16px, 1rem will be qual to 16px

- Rem is consistent. It behaves consistently and predictably like pixels but it respects user preferences when increasing/decreasing font sizes

## Percentages

- Often used with width/height as a way to consume a portion of the available space

## Which unit to use?

- Typography generally uses `rem`, because it has important accessibility benefits

- For properties that relate to the box model - `padding`, `border`, `margin` - use pixels. More intuitive than `rem` and no clear accessibility benefits

- For width/height, it depends on whether we want the element to be a fixed size or a relative size. Use pixels or percentage respectively

- For colour, use HSL as it is very intuitive
