# Button group

The button group is a ready-made set of buttons that sit together, usually in the footer of a modal or drawer. It holds a secondary button, a main action, and a tertiary "…" button for extra actions.

## Why it's a component

- Same order and spacing in every modal and drawer, so no screen ends up a little different.
- It builds in the hierarchy rules: one main action per group, next to a secondary.
- Switching a confirm from dark blue to red is one variant change, not a rebuild.
- Designers drop it in, and devs build it once and reuse it.

## Rules

- **Order:** the tertiary "…" button sits on the left, then the secondary, then the main action on the right.
- **Variants:** `primary` (dark blue) and `destructive` (red). The main action is red only for actions that delete or can't be undone.
- **Sizes:** `md` and `lg`. There is no `sm` in the first pass because it has few use cases.
