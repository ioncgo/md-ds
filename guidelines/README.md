# Design System Docs

Rules for the Manager Dashboard UI. One file per rule set or component.

## Folders

- `foundation/` has the basics: colors, typography, spacing, icons, corner radius. All written, plus accessibility.
- `general-rules/` has rules that apply across components. Empty for now.
- `components/` has one file per component.
- `compositions/` has rules for how components work together, like the [table](compositions/table.md).

## Naming

Use the same names as the Figma file. If a name in Figma is wrong, fix it in Figma first, then here.

## Open items

- Button: size `lg` has no use assigned yet.
- Button: loading state is not defined. To be decided with the team.
- Button split: no dark blue variant and no focused state in Figma.
- Chip: selected chips are named `state6`, `state7`, `state8` in Figma. Rename them to match the unselected ones.
- Tooltip: no placement rule yet.
- Dialog: the Delete order dialog in Figma says "cancel this order". It should say delete.
- Table: hug column width is set by the widest of header or content. Undecided if content alone should set it, with the header wrapping.
- Search: which size to use inside menus is not decided.
- Dialog and drawer: drawer rules are not written yet.
- Radius: no component is bound to a radius variable, so the scale can't actually be changed from one place yet. See `foundation/radius.md`.
- Badge: no rule for which color means what. `strong`/teal and `strong`/purple look like they fail contrast with white text. See `components/badge.md`.
- Spacing: no page/layout spacing scale. Table density is documented in `compositions/table.md`, not here. See `foundation/spacing.md`.
- Icons: small UI icon source is not identified, no icon-to-name mapping, no size scale, no color/stroke rule. See `foundation/icons.md`.
- Typography: `body/xxs` (11px) breaks the 12px minimum, no usage rules per style, no mono style. See `foundation/typography.md`.
- Colors: no semantic tokens, no status colors, and variable scopes are not set. See `foundation/colors.md`.
