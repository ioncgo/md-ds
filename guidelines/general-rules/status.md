# Status and feedback

A status is never shown by color alone. Every status needs an icon, a text label, or both — color reinforces it, it doesn't carry it (A11Y-17 in [Accessibility](../foundation/accessibility.md)).

## The five categories

| Category | Color | Meaning | Examples |
| --- | --- | --- | --- |
| **Success** | Green | Something finished and went right | Completed, healthy, connected |
| **Warning** | Yellow | Not broken, but needs attention soon | Needs review, nearing a limit |
| **Error** | Red | Failed, destructive, or blocked | Failed, destructive action, blocked |
| **Info** | Blue | A neutral update, or acknowledging something went well without calling it a full "success" | A neutral choice was made, good work / heads up |
| **Neutral** | Grey (`neutral/*`) | No judgment attached — not positive, not negative | Default state, system-generated, not yet known |

These match the semantic tokens already in Figma: `text/success`, `text/warning`, `text/error`, `text/information`. There's no `text/neutral-status` token yet — see open items.

## Rules

- **Every status has a fixed icon.** The same category uses the same icon everywhere. Don't use one icon for "error" in a toast and a different one in a badge.
- **Icon or label, not color alone.** A colored dot by itself is not a status. Pair it with a label (preferred), an icon, or both.
- **Pick the category by meaning, not by which color looks good.** "Nearing a limit" is a warning even if green would look calmer next to it.
- **Don't invent a sixth category.** If something doesn't fit Success, Warning, Error, Info or Neutral, that's a sign that what you're showing isn't a status.
- **A badge, on its own, is not a status indicator** — not even `badge-icon-only` without a label next to it. See where this shows up.

## Where this shows up — and where it doesn't

- **Not `badge-text` or `badge-numeric`.** These two [Badge](../components/badge.md) kinds are general-purpose labels, not system status. A badge's color is looser than the categories above — red can read as "critical" without meaning the formal Error status, green can read as "good" without being a declared Success state. Don't treat a badge's color as if it were announcing one of the five categories here.
- **System status is a standalone icon, in the category's color, always next to a text label.** Icon alone isn't enough — same rule as above, just spelled out for the icon case specifically.
- **The one exception: `badge-icon-only`.** Of the three badge kinds, only `badge-icon-only` can carry a system status — but it still needs a text label next to it to do so, same as any other status icon. A `badge-icon-only` sitting on its own, with no label nearby, is not a valid status indicator. It's the icon-only shape being reused, not the badge component gaining a new exemption from the icon-or-label rule.
- **Icons:** pick one icon per category, from [Icons](../foundation/icons.md), and reuse it everywhere that status appears.

## Open items

- **No icon is chosen yet per category.** This doc says "the same icon everywhere," but doesn't name which icon that is for Success, Warning, Error, Info, or Neutral.
- **No semantic token for "neutral status" in Figma.** Success/Warning/Error/Info all have a `text/*` token. Neutral doesn't — decide whether it reuses `text/muted` or gets its own token.
- **Purple (`text/discovery`) isn't part of this doc's five categories.** Figma's theme collection has a `discovery` semantic color alongside warning/error/success/information. Confirm whether "discovery" is a sixth status category this doc is missing, or something else entirely (a feature-highlight color, say) that shouldn't be confused with status.
- **Teal has no assigned meaning**, status or otherwise. Still open from [Colors](../foundation/colors.md).
- **"Info" vs. "good work" are two different feelings sharing one color.** A neutral system update and a congratulatory note aren't the same thing, even if both default to blue here. Worth a second look once there are real examples of each.
