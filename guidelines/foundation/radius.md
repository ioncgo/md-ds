# Corner radius

## Scale

8 steps, with two modes: `round` (the default) and `square`.

| Variable | Round | Square |
| --- | --- | --- |
| `radius-none` | 0 | 0 |
| `radius-xs` | 2 | 0 |
| `radius-sm` | 4 | 0 |
| `radius-md` | 6 | 0 |
| `radius-lg` | 8 | 0 |
| `radius-xl` | 12 | 0 |
| `radius-xxl` | 16 | 0 |
| `radius-full` | 99 | 99 |

- **`square` mode zeroes every step except `radius-full`.** This looks like a built-in way to switch the whole product to sharp corners without touching every component, while keeping pills and circles (avatars, dots, the full-round badge shape) round in either mode.
- **`round` is the default mode.** Nothing in the file currently switches to `square`. Treat it as available, not active.

## What components actually use

Checked corner radius directly on button, input, chip, badge, checkbox and dialog components. None of them are bound to a `radius` variable — every one is a plain number set by hand.

| Component | Corner radius | Matches |
| --- | --- | --- |
| Button | 4 | `radius-sm` |
| Chip | 4 | `radius-sm` |
| Checkbox | 4 | `radius-sm` |
| Badge | 99 | `radius-full` |
| Dialog (the popup itself) | 8 | `radius-lg` |
| Input | 0 | `radius-none` |

The values line up with scale steps, but since nothing is bound, a change to `radius-sm` in the variable wouldn't move the button, the chip, or the checkbox. See open items.

## Rules

- Use the variable, never a raw number, once components are bound to it (see open items — this isn't true yet).
- Don't introduce a corner radius outside this scale.
- `radius-full` is for pills and circles only (badges, avatars, dots), not for general rounding.

## Open items

- **No component is bound to a radius variable.** Button, chip, checkbox, badge, dialog and input all use a hardcoded number that happens to match a step on the scale. Bind them, so the scale can actually be changed from one place.
- **Input has 0 corner radius.** Every other interactive component in this check uses `radius-sm` (4). Confirm whether a sharp-cornered input is intentional or a miss.
- **`square` mode is unused.** It exists in the variable collection but nothing in the file switches to it. If there's no plan to ship a square-corners theme, it may not be worth keeping two modes.
- **No rule for which step is for what.** Nothing says, for example, that cards use `radius-lg` and controls use `radius-sm` — that's inferred here from what's already built, not written down as a rule.
