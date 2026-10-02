# Changelog

One line per change. Newest first.

## v0.5 (draft)

- General rules: status and feedback. Five categories (success, warning, error, info, neutral) and the icon-or-label rule. Corrected: badges don't carry system status, only `badge-icon-only` does, and only paired with a text label.
- Foundation: token structure. Three layers (primitives, semantic tokens, everything else) and the rule for which file consumes which. Found a few places Figma doesn't follow it yet.
- Dialog: moved from `components/` to `compositions/`, alongside Table.
- Foundation: icons. Corrected sourcing: used as a published Figma library, not copied in per icon. Dropped the per-icon status workflow.
- Foundation: icons. Added Carbon's own usage guidelines (sizing, color/contrast, touch targets, alignment, states) as our default until we write our own.
- Foundation: color primitives. Full hex reference for all 125 color steps, as an explicit exception to the no-hex-values rule in Colors.
- Foundation: corner radius. The 8-step scale, round/square modes, and which components actually use which step.
- Badge: variants (strong, subtle, outlined, ghost), hierarchy by visual weight, colors, sizes.
- Foundation: spacing. 4px base grid, Tailwind alignment, token rules, the x0-x32 scale.
- Foundation: icons. Source library (IBM Carbon, community), category list, status workflow, why one size per icon (Carbon v11).
- Foundation: typography. Font families, weights, and the 15 text styles.
- Foundation: accessibility and color contrast (WCAG 2.2 AA, rules A11Y-01 to A11Y-26, exception EX-01).
- Foundation: colors. Brand and support colors, no values.
- Table: moved to `compositions/` as one file. Order ID truncation, other text columns and badges, column sizing, container and scroll behavior, filtering menus.
- Filtering menus: search input when a menu has more than 5 options.
- Button: variants, hierarchy rules, sizes, states, labels and icons.
- Button group: order, variants, sizes.
- Button split: usage, variants, sizes, states.
- Chip: usage and states.
- Search: usage, sizes, states.
- Tooltip: usage.
- Dialog: structure, variants, closing rules.
