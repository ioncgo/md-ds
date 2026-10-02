# Typography

Figma files:

- Base variables: https://www.figma.com/design/qsvaDkP7lsiYk4KYtLxMlW/Foundation (collection `typography`)
- Text styles and their variables: https://www.figma.com/design/5nGbl24ZhF2RKmXg5dgtaN/Components (page `typography`)

The font is Inter. Hierarchy comes from size and weight.

## Font families

| Variable | Font | Use for |
| --- | --- | --- |
| `family/heading` | Inter | Headings. |
| `family/body` | Inter | Body text and everything else. |
| `family/mono` | Geist | Monospace text. The Order ID uses it, see [Table](../compositions/table.md). |

Use the family variable, never the font name. If the font changes, it changes in one place.

## Weights

| Variable | Value | Used by |
| --- | --- | --- |
| `weights/Regular` | 400 | Body styles. |
| `weights/Medium` | 500 | Body styles. |
| `weights/Semi Bold` | 600 | All heading styles. |
| `weights/Bold` | 700 | No style uses it. |

## Type styles

There are 15 text styles: 5 headings and 10 body styles (5 sizes, each in two weights). Apply a style, never set size, weight, or line height by hand.

### Headings

All headings are Inter Semi Bold. Letter spacing is slightly tighter as the size goes up.

| Style | Size | Line height | Letter spacing |
| --- | --- | --- | --- |
| `heading/xl` | 28 | 36 | -0.5 |
| `heading/lg` | 24 | 32 | -0.4 |
| `heading/md` | 20 | 28 | -0.3 |
| `heading/sm` | 16 | 24 | -0.2 |
| `heading/xs` | 14 | 20 | -0.15 |

### Body

Every body size comes in two weights: `400` (Regular) and `500` (Medium). Letter spacing is 0.

| Style | Size | Line height |
| --- | --- | --- |
| `body/lg/400`, `body/lg/500` | 16 | 24 |
| `body/md/400`, `body/md/500` | 14 | 20 |
| `body/sm/400`, `body/sm/500` | 13 | 20 |
| `body/xs/400`, `body/xs/500` | 12 | 18 |
| `body/xxs/400`, `body/xxs/500` | 11 | 14 |

- `body/md` is the default for dashboard body text. See [Accessibility](accessibility.md).
- Line height is about 1.4 to 1.5 times the size at every step, and bigger sizes use a bit less.
- Regular is for reading. Medium is for labels, and for text that needs weight without becoming a heading.

## Accessibility limits

From [Accessibility](accessibility.md):

- Never set text below 12px. Body text on dashboards starts at 14px (A11Y-04).
- Large text is 24px regular, or 18.66px bold and up (contrast thresholds).
- Don't make text lighter with opacity. Use a color token (A11Y-02).

`body/xxs` is 11px, which is under that limit. See open items.

## Open items

- **`body/xxs` is 11px.** A11Y-04 says never below 12px. Either the style is removed, or it's logged as an exception.
- **`body/sm` is 13px and `body/xs` is 12px.** Both are under the 14px that body text starts at. Decide where they're allowed, such as captions or helper text, and write it down.
- **No usage rules.** Nothing says which style is for a page title, a table cell, a label, or helper text.
- **`body/xl` has variables but no text style.** The 18px size (line height 26) exists in the variables. Either add the style or remove the variables.
- **No mono style.** The Order ID needs a monospace style. `family/mono` exists, but no text style uses it.
- **Bold (700) isn't used by any style.** Keep the variable or remove it.
- **Mixed variable binding.** Several text styles point at a variable from a different style. For example `body/md/400` takes its size from `body/md-14/500`. The values match today, but a change to one variable would move the wrong style. Also, the names differ: styles are `body/lg/500`, variables are `body/lg-16/500`.
- **Raw numbers.** The 13px and 11px sizes, the 11px line height, and all heading letter spacing values are typed in, not linked to a variable like the other sizes.
- **Two typography collections.** The Foundation file has 7 base variables, and the Components file has 85 variables that link to them. Confirm the Components file should be the one designers use.
