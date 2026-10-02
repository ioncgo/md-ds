# Button

Buttons have five variants, three sizes, and four states. Orange is for level 0 actions only, and dark blue covers most other primary actions.

## Variants

| Variant | Color | Use for |
| --- | --- | --- |
| `primary` | Orange (brand) | Level 0 primary action of a view. Only one per view. |
| `neutral-dark` | Dark blue (brand secondary) | Primary actions in modals, drawers, and most other UI. Calm, not in your face. |
| `destructive` | Red | Actions that delete or can't be undone. |
| `secondary` | White, with border | The second action next to a primary. |
| `tertiary` | No fill, no border | Low-key actions, like Cancel or Clear filters. |

## Hierarchy rules

- Never show two orange buttons in the same view. Two of them compete, and then neither is primary.
- Inside a modal or drawer, the primary action is dark blue, never orange.
- In a confirm dialog for a delete, the destructive button takes the primary spot.
- Pair a primary with a secondary or tertiary. Don't put two primaries side by side.

## Sizes

| Size | Height (px) | Use for |
| --- | --- | --- |
| `sm` | 28 | Tables, and other UI actions inside modals |
| `md` | 32 | Default |
| `lg` | 40 | Not assigned yet |

## States

- Default, hover, pressed, and focused. Focused shows the blue focus ring.
- There is no disabled state. If an action isn't available, hide it. If it needs input first, let the user click and show what's missing.
- Loading state is not defined yet. To be decided with the team.

## Labels and icons

- Labels are short, start with a verb, and use sentence case.
- Labels never truncate, same as badges.
- An icon is optional, on the left or the right of the label.
- An icon-only button needs a tooltip and an accessible name.
