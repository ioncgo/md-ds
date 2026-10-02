# Icons

This is the IBM Carbon icon library (a community file, not ours). We use it for enterprise-specific icons

## What's in the file

- **2,378 icons**, one 16×16 symbol each, grouped into 19 named categories: AI, App catalogue, Controls, Data, File, Formatting, Health, IBM, Instruments, Navigation, Operations, Senses, Status, Systems, Technology, Time, Toggle, Travel, User.
- It's a Figma Community file we don't own. We use it as a published library: the community file is published, and this design system uses the published icons directly, not a copy pasted into our own file.

## Where it fits

- **Small UI icons** (inside buttons, inputs, chips, tooltips — see [Button](../components/button.md), [Chip](../components/chip.md), [Search](../components/search.md)) are not covered by this file. See open items.

## Why one 16×16 symbol per icon

This matches how Carbon itself ships icons today. Reference: https://www.carbondesignsystem.com/getting-started/migrating/guide/overview

- **Old Carbon (v10):** every icon was exported at each size separately (16, 20, 24, 32...), as separate files. That's a lot of files, and it's not how this library is built.
- **Current Carbon (v11):** an icon is one component with a `size` prop. The 16×16 artwork is the single source, and code scales it. That's why the Figma library has one 16×16 symbol per icon instead of a size per icon.
- **What this means for us:** "large" isn't a different icon asset to pick, it's the same icon rendered bigger. In code, that's the Carbon icon component's `size` prop; in Figma, that's the instance resized, not swapped for another icon.

## Carbon's own icon guidelines

Reference: https://www.carbondesignsystem.com/building-blocks/foundations/icons/guidelines

Carbon publishes its own usage rules for this icon set. We haven't adopted all of them yet (see open items), but they're the reasonable default until we write our own:

- **Sizes:** 16px and 20px are the standard sizes, optimized to feel balanced next to 14px and 16px type. 24px and 32px exist for larger use. Keep the icon-to-text size ratio consistent; don't distort it.
- **Color:** an icon is monochromatic — one solid color, not multiple. Match the icon's color to the color of the text next to it, and meet the same 4.5:1 contrast rule text does.
- **Alignment:** center-align an icon with the text next to it.
- **States:** the icon itself doesn't change for hover, pressed, focused, etc. Only its background or container does.

## Rules

- Resize the same icon for large use, don't look for a separate "large" asset. See above.
- Scale in fixed steps (see spacing/sizing in `units`, not written yet), not freely.
- Icon-only controls need an accessible name and, outside the dashboard's own controls, a tooltip. See [Tooltip](../components/tooltip.md) and A11Y-26 in [Accessibility](accessibility.md).
- Icons never carry meaning alone. Status and selection need a second cue too (A11Y-17, A11Y-18 in [Accessibility](accessibility.md)).
- An icon is one solid color. Match it to the adjacent text color, and meet 4.5:1 contrast (A11Y-01 in [Accessibility](accessibility.md)). See Carbon's guidelines above.

## Open items

- **No in-product icon size scale, ours specifically.** Carbon names 16/20/24/32px as its sizes, but nothing here says which of those (or what else) counts as our "large" vs. our regular UI size.
- **Small UI icons aren't sourced yet.** Buttons, inputs, chips and search all reference an icon, but no file is named for the regular interaction-size icon set. Confirm whether that's this same library at a smaller size, or a separate source.
- **No icon-to-name mapping written down.** The library has 2,378 icons across 19 categories; this doc doesn't list which icon is used for which product concept. Add that once icons are actually picked for use.
- **What "published" means for this library isn't written down.** Confirm how updates to the community file reach us: do we get them automatically once the author republishes, or does someone need to pull in the update?
- **Stroke weight isn't covered**, by us or by Carbon's own guidelines page.
- **Carbon's icon color rule isn't fully reconciled with our badge/status colors.** "Match text color" is clear for an icon next to a label, but less clear for a status icon (e.g. a red icon next to black text) — confirm how that case works.
