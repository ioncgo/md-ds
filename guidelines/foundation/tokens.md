# Token structure

Three layers. Each layer only talks to the one next to it.

1. **Primitives** — the raw palette: `brand/orange/300`, `neutral/700`, `red/600`, and the same idea for type, spacing and radius. Defined in the Foundation Figma file. See [Colors](colors.md), [Primitives](primitives.md), [Typography](typography.md), [Spacing](spacing.md), [Corner radius](radius.md).
2. **Semantic tokens** — named by role, not by value: `text/error`, `background/surface`, `border/subtle`. Defined in the Components Figma file, and built by pointing at primitives. This also covers component-specific tokens, like `component/badge/subtle/bg-red` or `component/button/primary/bg-default` — narrower in scope, but the same layer, same file.
3. **Everything else** — compositions, patterns, product screens. These consume semantic and component tokens only.

## The rule

- **Primitives are consumed in exactly one place: the Components file.** Nothing else reads `red/600` or `neutral/300` directly.
- **Everything downstream of Components uses a semantic or component token**, never a primitive. A composition doc, a layout, a product screen reaches for `text/error` or `component/badge/subtle/bg-red`, not `red/700` or `red/100`.
- **If the token you need doesn't exist, that's a reason to add one to the Components file**, not a reason to reach past it into a primitive.

This keeps the palette swappable from one place. If a primitive shade changes, the Components file is the only place that could be affected — not every doc, pattern or screen that happened to reference a raw color.

## What's already in Figma

The Components file has a `theme` collection with 202 variables doing exactly this: semantic tokens like `text/*`, `foreground/*`, `background/*`, `border/*`, `brand/*`, plus component-scoped tokens like `component/badge/*`, `component/button/*`, `component/input/*`, `component/chip/*`, and more. This structure exists already; it just hadn't been written down anywhere until now.

## Related

[Status and feedback](../general-rules/status.md) names what each status color (success, warning, error, info, neutral) means, and maps onto the `text/success`, `text/warning`, `text/error`, `text/information` semantic tokens here.

## Open items

Checked where the 202 `theme` variables actually point, to see if the rule above already holds. It mostly does, but not everywhere:

- **Some component tokens skip the semantic layer and alias a primitive directly:**
  - `component/badge/strong/bg-teal` → `teal/500`, `component/badge/strong/bg-purple` → `purple/500` (every other `badge/strong/bg-*` goes through a semantic token like `foreground/error`)
  - `component/badge/dot/bg-teal` → `teal/500`, `component/badge/dot/bg-purple` → `purple/500` (same pattern)
  - `component/button/primary/bg-default` → `brand/orange/400`, `component/button/primary-dark/bg-default` → `brand/deep navy/950`
  - `component/button/split/border-default` → `brand/orange/500`
  - `component/chip/*` and `component/segmented/*` → straight to `neutral/*` steps
  - `component/input/border-default` → `neutral/300`, `component/toggle/bg-default` → `neutral/500`

  None of these are wrong-looking values, they just don't go through a semantic token the way most of the rest of the file does. Worth a pass to decide if these get a semantic token too, or if component tokens are allowed to touch primitives directly (in which case, write that down as part of the rule above, not just here).
- **`brand/brand-bold`, `brand/brand-muted`, `brand/brand-subtle` and `brand/brand-inverted` all resolve to `blue/*` primitives**, not to the orange/deep-navy brand family. `brand/brand` itself correctly resolves to `brand/deep navy/500`. This looks like a copy-paste mistake; worth checking in Figma.
- **`background/discovery` and `background/discovery-bold` are both `purple/100`.** Every other pair (`warning`/`warning-bold`, `error`/`error-bold`, `success`/`success-bold`, `information`/`information-bold`) steps up one shade for `-bold`. Discovery doesn't. Likely a bug.
- **`component/calendar/bg` and `component/calendar/fg` don't resolve to a named variable at all** — they read back as a raw value, not an alias to anything else in the file. Worth checking whether that's a hardcoded color that should be a token like everything else here.
