# Colors

## No values in these docs

Hex codes are not written here, on purpose.

- **Figma is the source of truth.** The values live in the Figma variables. A copy here is a second place to update, and it goes out of date the first time a shade changes.
- **These docs are not published.** They are not a spec anyone ships from, so a value written here adds nothing and can only be wrong.
- **Hex codes in docs end up in code.** If a value is visible here, someone will paste it instead of using the variable, and the change is then missed when the color is updated.

Refer to colors by variable name, like `brand/orange/300`. To check a value, open the variable in Figma.

## Brand colors

Two colors are the brand. Both have a full scale from `50` to `950`.

| Color | Variables | Role |
| --- | --- | --- |
| Orange | `brand/orange/50` to `950` | Brand. Level 0 actions only. See [Button](../components/button.md). |
| Deep navy (dark blue) | `brand/deep navy/50` to `950` | Brand secondary. Most other primary actions. |

- Orange is rare on purpose. If it's everywhere, nothing stands out. Never use orange in a dialog.
- Dark blue is the calm default for primary actions in modals, drawers, and most other UI.

## Support colors

Everything else supports the brand and never competes with it. Each has a full scale from `50` to `950`.

| Color | Variables | Use for |
| --- | --- | --- |
| Red | `red/*` | Destructive actions and error text. See [Button](../components/button.md) and [Dialog](../components/dialog.md). |
| Yellow | `yellow/*` | Not assigned yet. |
| Green | `green/*` | Not assigned yet. |
| Teal | `teal/*` | Not assigned yet. |
| Blue | `blue/*` | Links (`blue/600`, hover `blue/800`) and the focus ring. |
| Purple | `purple/*` | Not assigned yet. |
| Neutral | `neutral/*` | Greys. Not assigned yet. Scale is `25` to `950`. |

Only red and blue have a use written down so far. The rest are in the file and ready, but their jobs are not decided. See open items.

## Other variables

| Group | Variables | Use for |
| --- | --- | --- |
| Black and white | `b&w/white`, `b&w/black`, `b&w/transparent` | Fixed values. |
| Alpha dark | `alpha/dark/50` to `1000` | Dark overlays that let what's underneath show through. |
| Alpha light | `alpha/light/50` to `1000` | Light overlays that let what's underneath show through. |

## Rules

- Use the variable, never a hex value.
- Use the brand colors for brand moments only. Use support colors for meaning, not decoration.
- Red means destructive or error. Don't use it for anything else.
- Contrast, focus, and status rules are in [Accessibility](accessibility.md).

## Open items

- There are no semantic tokens yet (like `text/primary` or `surface/default`). Every variable is a raw palette step, so nothing says which step is for which job.
- Every color variable has the scope set to "All scopes". They show up in every color picker, including where they shouldn't (a text color as a fill).
- `brand/orange/50` is missing the "Generated from Tailwind Color System" description the rest have, so it may have been added by hand. `brand/deep navy/50` has a cyan tint compared to the rest of its scale. Check that both were meant.
- No dark mode. The collection has a single mode.
- Yellow, green, teal and purple have no assigned use yet. Status colors (warning, success, error) are not defined.
