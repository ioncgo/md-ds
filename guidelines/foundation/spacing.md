# Spacing

The Manager Dashboard design system uses a 4px base grid. Structural spacing is always a multiple of 4px, with one documented exception: three half-steps (`x0-5`, `x1-5`, `x2-5`) for micro-spacing. No other exceptions.

Tokens match Tailwind CSS's spacing scale, both in the numbers (`x1` = 4px, `x4` = 16px, same as Tailwind's `1` and `4`) and in the half-step naming (`x0-5`, `x1-5`, `x2-5`, same pattern as Tailwind's `0.5`, `1.5`, `2.5`). Tailwind works the same way: a half-step scale layered under a 4px grid, not a pure 4px grid.

## Scale

19 steps, from `x0` to `x32`. Each one is a value from the `units` collection (see [Typography](typography.md) for how `units` is also used for font sizes).

| Variable | Value |
| --- | --- |
| `x0` | 0 |
| `x0-5` | 2 |
| `x1` | 4 |
| `x1-5` | 6 |
| `x2` | 8 |
| `x2-5` | 10 |
| `x3` | 12 |
| `x4` | 16 |
| `x5` | 20 |
| `x6` | 24 |
| `x8` | 32 |
| `x9` | 36 |
| `x10` | 40 |
| `x12` | 48 |
| `x16` | 64 |
| `x20` | 80 |
| `x24` | 96 |
| `x28` | 112 |
| `x32` | 128 |

- The name is the multiple of 4, not the pixel value. `x4` is 16px, `x8` is 32px. `x0-5`, `x1-5` and `x2-5` are the half-steps (2, 6, 10).
- Scoped to gap only (`GAP`), so these variables only show up in spacing fields in Figma, not in every number field. This is the pattern [Colors](colors.md) is missing (see its open items).
- Use the variable, never a raw number. If spacing changes, it changes in one place.

The table has its own density-based spacing (`data-grid`), not on this scale. See [Table](../compositions/table.md).

## Rules

- **Always use a token.** If the spacing you need isn't in the table above, round to the nearest token.
- **Never use an arbitrary value**, like `p-[13px]`. If you find yourself doing this, flag it.
- **Never hardcode a px value** in inline styles.
- **All spacing is a multiple of 4px, except the three half-steps** (`x0-5`, `x1-5`, `x2-5`), which exist for micro-spacing only.
- **`x0-5` (2px) is micro-spacing only.** Don't use it for anything structural. The same goes for `x1-5` and `x2-5`.
- **`x1` (4px) is the minimum layout unit.** Don't go below it for anything structural. The half-steps are the one allowed exception, and only for micro-spacing.

## Open items

- **No layout spacing scale.** `x*` covers gaps between things. Page margins, section spacing, and card padding aren't called out anywhere.
- **Corner radius and border width aren't covered here.** They're separate collections (`radius`, `border`), not part of spacing. Worth their own foundation file once there's a rule to write, not just a list of values.
- **The table's `data-grid` density variables are documented in [Table](../compositions/table.md), not here.**
