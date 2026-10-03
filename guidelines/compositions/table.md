# Table

Truncation, column sizing, scrolling, and filtering menus for the table.

## Order ID truncation

Only the Order ID column (first column) uses middle truncation. No other column does.

- **When:** the ID is longer than 20 characters. At 20 or fewer, show the full ID.
- **What to show:** the first 7 characters, then `…`, then the last 8 characters. The result is never longer than 16 characters.
- **Example:** `ORD-2024-00481-EU-WH3` shows as `ORD-202…1-EU-WH3`.
- **Why the middle:** many IDs start the same way, so the end is what tells rows apart.
- **Ellipsis:** use the single `…` character, not three dots.
- **Full value:** show it in a tooltip on hover and on keyboard focus. See [Row hover](#row-hover) for the copy button that comes with it.
- **Screen readers:** read the full ID, not the shortened one.
- **Font:** monospace, so shortened IDs line up.
- **Data:** search, sort, filter, and export always use the full ID.

## Row hover

Hovering a row does two separate things, both in the Order ID column. Neither is hover-only — both need a keyboard equivalent.

**View details**

- The "view details" icon has its own spot, separate from the expand/collapse chevron. It doesn't replace the chevron, and the chevron doesn't move to make room for it.
- It's only visible while the row is hovered. Move off the row, and it's gone again.
- Clicking it opens the row's details.
- This needs a keyboard path too: tabbing to the row (or to the icon itself) should make the same icon reachable and usable, not only on mouse hover.
- Works the same whether the row has children or not. A leaf row has no chevron, but still has the view-details spot.

**Copy the ID**

- Only when the ID is truncated: hovering or focusing it shows the tooltip from [Order ID truncation](#order-id-truncation) and a copy button together, the button sitting after the value.
- Clicking the button copies the full ID, never the shortened one.
- An ID short enough to show in full doesn't get a copy button. There's nothing truncated to copy out.

## Other text columns and badges

Every other text column cuts off at the end. Badges are never truncated.

- **Text columns:** cut off at the end with `…` when the text doesn't fit the column. Show the full text in a tooltip.
- **Badges:** never truncate. A cut-off status loses the one thing the badge is there to say.
- **Long badge:** keep it on one line and let the column hug it. If it gets too wide, set a max width and wrap to two lines.
- **Last resort:** if wrapping breaks the layout, fall back to end truncation with a tooltip.

## Column sizing

Columns are either hug or fraction. Hug columns are measured first, and fraction columns share what is left.

**Hug columns** (badges, time, dates, quantities, Order ID, actions)

- Width is the widest of the header text or the longest content, plus padding.
- Never truncate and never shrink below that width.
- Because data is paginated, measure against the longest possible value, not the visible page. Use the full status list and the longest time format. This way the column never jumps when the user changes pages.
- Order ID hugs predictably because it is capped at 16 characters after truncation.

**Fraction columns** (names, locations, notes, descriptions)

- They share the space left after hug columns are measured.
- Each column uses one weight from the table below, chosen by how much content it usually holds.
- Text cuts off at the end with `…` and a tooltip.

| Weight | Min width (px) | Use for |
| --- | --- | --- |
| `0.5fr` | 120 | Short text |
| `1fr` | 120 | Standard text |
| `2fr` | 200 | Long text, like notes |

No `0.33fr`. With a minimum width in place, a third-sized column hits its minimum right away and behaves like `0.5fr`.

## Container and scroll behavior

The table lives in its own container and scrolls there. The page never scrolls because of the table.

**Container**

- It fills the full height of the content area, which is everything to the right of the left nav.
- It scrolls on its own, both vertically and horizontally.
- Columns never shrink below their minimums. When the container is too narrow, horizontal scroll appears.

**Sticky parts**

- The header row sticks to the top of the container.
- The Order ID column sticks to the left of the container.
- The top-left cell (Order ID header) sticks in both directions and sits on the highest layer.
- Header and pinned column have solid backgrounds, so rows don't show through when they scroll underneath.
- The pinned column gets a shadow on its right edge, only after the user has scrolled sideways.

**Pagination**

- The pagination bar is pinned to the bottom of the container, outside the scroll area.
- Rows scroll between the sticky header and the pagination bar.

**Left nav collapse**

- When the nav collapses or expands, the container width changes.
- Fraction columns resize on their own. Hug columns stay the same.
- Horizontal scroll turns on or off based on the new width.

## Filtering menus

A filter menu with more than 5 options gets a search input. With 5 or fewer, show the options only.

See [Search](../components/search.md) for the input itself.

- **Search input:** sits at the top of the menu, above the options.
- **Focus:** the input is focused as soon as the menu opens, so the user can type right away.
- **Matching:** the list filters as the user types. Ignore upper and lower case, and match anywhere in the option text.
- **No matches:** show a short "No results" message in the list.
- **Clear:** show a clear (x) button in the input once it has text.
- **Long lists:** set a max height for the options and scroll inside the menu. The search input stays pinned at the top while the options scroll.
