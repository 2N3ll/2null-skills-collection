# Frontend design system and art direction

Use this guide when creating a new page or substantially redesigning an existing interface.

## Start with a visual thesis

Write one sentence that describes the visual concept. Examples:
- Editorial product launch: oversized typography, restrained palette, confident whitespace, and cinematic image crops.
- Technical developer tool: dense but structured information, crisp borders, monospace accents, and precise interaction feedback.
- Playful consumer product: expressive type, vivid accents, tactile controls, and friendly motion.

Do not combine unrelated visual styles without a reason.

## Hierarchy

- Give every page one primary focal point.
- Use scale, weight, contrast, alignment, and whitespace to establish reading order.
- Keep headings concise and supporting copy readable.
- Avoid making every section equally loud.
- Use consistent content widths and alignment.
- Let important content breathe; use density intentionally for data-heavy interfaces.

## Typography

- Choose typefaces for character and legibility, not novelty alone.
- Use a clear type scale and a limited number of weights.
- Keep body copy comfortable to read.
- Use line length, line height, and letter spacing deliberately.
- Avoid excessive all-caps text and arbitrary font-size variation.
- Use system fallbacks and avoid blocking rendering on optional fonts.

## Colour and surfaces

- Define semantic tokens (background, surface, text, muted text, border, primary, accent, success, warning, danger).
- Check contrast for normal and small text.
- Use gradients, blur, glow, shadows, and transparency only when they support the concept.
- Avoid using gradients as a substitute for composition.
- Do not rely on colour alone to communicate state.

## Layout and responsive behaviour

- Define a spacing scale and breakpoints that match the content.
- Use CSS Grid and Flexbox according to layout needs.
- Avoid fixed widths that cause horizontal overflow.
- Reflow navigation, columns, and media intentionally on smaller screens.
- Check long headings, localisation, zoom, and dynamic content.
- Prefer fluid sizing with sensible min/max constraints when appropriate.

## Components and consistency

- Establish shared button, input, card, navigation, and section patterns.
- Use consistent radii, borders, shadows, and focus treatments.
- Avoid wrapping every element in a card.
- Use semantic HTML and native controls when they are sufficient.
- Keep components composable and avoid abstractions that obscure simple markup.

## Images and visual assets

- Use imagery that supports the content and art direction.
- Preserve image aspect ratios and use intentional crops.
- Provide meaningful alt text for informative images and empty alt text for decorative images.
- Avoid placeholder imagery in final work unless requested.
- Do not invent brand marks or use unlicensed assets.

## Final design review

Ask:
1. Is the main purpose immediately clear?
2. Is there a distinct visual identity?
3. Is the hierarchy obvious without relying on animation?
4. Does the layout work at narrow widths?
5. Are controls visually and behaviourally consistent?
6. Is every decorative effect earning its place?
