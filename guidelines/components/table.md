# Table

Truncation rules live in [Truncation](../general-rules/truncation.md).

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
