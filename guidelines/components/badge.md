# Badge

A badge is a small label that marks a status or calls out something about a row or item. It's not clickable.

## Kinds

| Component | Content | Variants |
| --- | --- | --- |
| `badge-text` | Icon (optional) + text | `strong`, `subtle`, `outlined`, `ghost` |
| `badge-numeric` | A count only | `strong`, `subtle`, `outlined` |
| `badge-icon-only` | An icon only | `strong`, `subtle`, `outlined` |

Every kind comes in 7 colors (`neutral`, `red`, `yellow`, `green`, `blue`, `teal`, `purple`) and 3 sizes (`sm`, `md`, `lg`).

## Hierarchy

The four variants are a visual-weight ladder, strongest to quietest: `strong` → `subtle` → `outlined` → `ghost`.

- **`strong`** (solid fill, white text/icon) is the strongest variant on purpose. Use it to flag something the manager needs to act on — the highest-priority call to attention in the row or card. Don't use `strong` for routine, already-settled status.
- **`subtle`** (tinted background), **`outlined`** (border only) and **`ghost`** (text/icon only, no fill or border) are for everything else: supporting information, or statuses that are secondary or tertiary to whatever `strong` is flagging. Use them for the normal, non-urgent states a dashboard shows most of the time.

Because `strong` is reserved for what needs action, don't reach for it to make a badge "stand out" visually. If every badge is `strong`, nothing is.

## Status

A badge is not how system status (success, warning, error, info, neutral) gets communicated — see [Status and feedback](../general-rules/status.md). `badge-text` and `badge-numeric` colors are general-purpose and looser than that: red can mean "critical" without being the formal Error status, green can mean "good" without being a declared Success. Don't read a badge's color as a status announcement.

The one exception is `badge-icon-only`, which can stand in for a status icon — but only when it's paired with a text label next to it. On its own, it's not a status indicator either.

## Rules

- Pick the variant by what the badge is for, not by what looks good. A settled, no-action status is never `strong`, even if `strong` happens to match the brand color better.
- One `strong` badge should read as more urgent than any `subtle`, `outlined` or `ghost` badge next to it. If a screen needs more than one level of "needs attention," that's a sign the hierarchy needs a second strong-adjacent option, not more `strong` badges.
- Badges are never truncated. See [Table](../compositions/table.md).
- A badge is not a button. If it needs to be clickable, it's the wrong component.
- Icon-only badges still need an accessible name (A11Y-26 in [Accessibility](../foundation/accessibility.md)).

## Open items

- **Teal and purple still have no assigned meaning**, even the looser badge kind of meaning the other five colors have. See [Colors](../foundation/colors.md).
- **Two `strong` colors look like they don't pass contrast.** Checked white text against the `strong` fill colors in Figma:
  - `strong`/teal: ~2.5:1 — clearly fails, even for large text.
  - `strong`/purple: ~4:1 — fails 4.5:1 for normal text, badge text at these sizes isn't "large text" per [Accessibility](../foundation/accessibility.md).
  
  Every other `strong` color (red, yellow, green, blue, neutral) passes at roughly 5:1 or better. Decide whether `strong`/teal and `strong`/purple get a darker fill (the way [Accessibility](../foundation/accessibility.md) darkened orange), or whether they're avoided until fixed.
- **`badge-numeric` and `badge-icon-only` have no `ghost` variant.** Only `strong`, `subtle`, `outlined` exist for these two. If the hierarchy in this doc applies to all three kinds, `ghost` is either missing from Figma or intentionally text-badge-only; confirm which.
- **A `dot` component exists in the same Figma page** (7 small circles) but every instance is plain white with no color variants wired up. Unclear if it's a status dot meant to pair with badges, or leftover/unfinished. Not documented here until it's clearer.
- **No rule for which size to use where**, same open item as [Search](search.md) has for its own sizes.
