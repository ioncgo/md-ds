# Icons

This is the IBM Carbon icon library (a community file, not ours). We use it for large icon variants and for enterprise-specific icons

## What's in the file

- **2,378 icons**, one 16×16 symbol each, grouped into 19 named categories: AI, App catalogue, Controls, Data, File, Formatting, Health, IBM, Instruments, Navigation, Operations, Senses, Status, Systems, Technology, Time, Toggle, Travel, User.
- Every icon ships in a "card" that also carries a build **status**: Not started, WIP, Review, Approved, Attention, or Published. Not every icon in the library is finished. Check an icon's status before using it.
- It's a Figma Community file we don't own. Icons are brought in by copying them into our own file, not by linking the community file directly.

## Where it fits

- **This library:** large icon use and enterprise/product icons
- **Small UI icons** (inside buttons, inputs, chips, tooltips — see [Button](../components/button.md), [Chip](../components/chip.md), [Search](../components/search.md)) are not covered by this file. See open items.

## Why one 16×16 symbol per icon

This matches how Carbon itself ships icons today. Reference: https://www.carbondesignsystem.com/getting-started/migrating/guide/overview

- **Old Carbon (v10):** every icon was exported at each size separately (16, 20, 24, 32...), as separate files. That's a lot of files, and it's not how this library is built.
- **Current Carbon (v11):** an icon is one component with a `size` prop. The 16×16 artwork is the single source, and code scales it. That's why the Figma library has one 16×16 symbol per icon instead of a size per icon.
- **What this means for us:** "large" isn't a different icon asset to pick, it's the same icon rendered bigger. In code, that's the Carbon icon component's `size` prop; in Figma, that's the instance resized, not swapped for another icon.

## Rules

- Use an icon from this library only if its status is Published. Anything earlier (WIP, Review, Attention) is not final.
- Resize the same icon for large use, don't look for a separate "large" asset. See above.
- Scale in fixed steps (see spacing/sizing in `units`, not written yet), not freely.
- Icon-only controls need an accessible name and, outside the dashboard's own controls, a tooltip. See [Tooltip](../components/tooltip.md) and A11Y-26 in [Accessibility](accessibility.md).
- Icons never carry meaning alone. Status and selection need a second cue too (A11Y-17, A11Y-18 in [Accessibility](accessibility.md)).

## Open items

- **No in-product icon size scale.** Nothing here says what px values count as "large" vs. regular UI size, even though both are the same icon at different sizes.
- **Small UI icons aren't sourced yet.** Buttons, inputs, chips and search all reference an icon, but no file is named for the regular interaction-size icon set. Confirm whether that's this same library at a smaller size, or a separate source.
- **No icon-to-name mapping written down.** The library has 2,378 icons across 19 categories; this doc doesn't list which icon is used for which product concept. Add that once icons are actually picked for use.
- **Status isn't tracked per use.** An icon pulled in today could later move backward in its own status (e.g. get flagged "Attention"). There's no process yet for re-checking icons already copied into our file.
- **No color or stroke rule for icons.** Nothing here says icon color (e.g. tied to `neutral/*`, or to the surrounding text color) or stroke weight.
