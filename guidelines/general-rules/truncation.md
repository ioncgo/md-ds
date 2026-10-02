# Truncation

## Order ID truncation

Only the Order ID column (first column) uses middle truncation. No other column does.

- **When:** the ID is longer than 20 characters. At 20 or fewer, show the full ID.
- **What to show:** the first 7 characters, then `…`, then the last 8 characters. The result is never longer than 16 characters.
- **Example:** `ORD-2024-00481-EU-WH3` shows as `ORD-202…1-EU-WH3`.
- **Why the middle:** many IDs start the same way, so the end is what tells rows apart.
- **Ellipsis:** use the single `…` character, not three dots.
- **Full value:** show it in a tooltip on hover and on keyboard focus. Add a copy button for the full ID.
- **Screen readers:** read the full ID, not the shortened one.
- **Font:** monospace, so shortened IDs line up.
- **Data:** search, sort, filter, and export always use the full ID.

## Other text columns and badges

Every other text column cuts off at the end. Badges are never truncated.

- **Text columns:** cut off at the end with `…` when the text doesn't fit the column. Show the full text in a tooltip.
- **Badges:** never truncate. A cut-off status loses the one thing the badge is there to say.
- **Long badge:** keep it on one line and let the column hug it. If it gets too wide, set a max width and wrap to two lines.
- **Last resort:** if wrapping breaks the layout, fall back to end truncation with a tooltip.
