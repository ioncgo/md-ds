# Design System Docs

Rules for the Manager Dashboard UI. One file per rule set or component.

## Folders

- `foundation/` has the basics: colors, typography, spacing, icons. Empty for now.
- `general-rules/` has rules that apply across components, like truncation.
- `components/` has one file per component.

## How to update

1. Edit the file.
2. Commit with a clear message, like `Dialog: added closing rules`. That message is the history.
3. Add one line to `CHANGELOG.md`.
4. When you hand something to devs, tag a release: `git tag v1.0` and push the tag.

## Naming

Use the same names as the Figma file. If a name in Figma is wrong, fix it in Figma first, then here.

Figma file: https://www.figma.com/design/5nGbl24ZhF2RKmXg5dgtaN/Components

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
- Foundation: not written yet.
