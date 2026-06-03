# Implementation Plan

Goal: Simplify the QMD hardware simulator section and add SVG interactivity.

## Proposed Changes

### `assets/js/custom/mobo.js`
- Export a new function `bindMoboInteractivity(tabsetSelector)`
- This function will:
  - Inject CSS for SVG hover effects (`cursor: pointer`, `filter: brightness`) on specific IDs (`#part-ssd`, `#part-ram`, `#cpu-l3`, etc.).
  - Bind `click` event listeners on these SVG elements.
  - When clicked, find the corresponding `nav-link` in the Quarto tabset using the label string, and trigger a click on it to switch the active tab.

### `index.qmd`
- Remove the massive old layout block (`L606-L844`) and the draft "Better version" (`L569-L601`).
- Replace it with a consolidated, clean implementation matching the user's horizontal table-like layout.
- Use raw HTML for the progress bars inside the tabs to keep the Markdown clean and perfectly styled.
- Hook up `bindMoboInteractivity(".mobo-tabset")` in the OJS execution cell.

## Verification
- Verify that `mobo.js` exports the function.
- Verify QMD renders cleanly without syntax errors.
