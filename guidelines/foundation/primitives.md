# Color primitives

The raw palette: every step of every color in the `color` collection. For which colors are brand vs. support, and the rules for using them, see [Colors](colors.md).

**This file is the one exception to "no hex values" in [Colors](colors.md).** Everywhere else, colors are referred to by variable name only, because Figma is the source of truth and a second copy of a value goes stale. This file exists anyway, as a single reference snapshot, so the full palette is readable without opening Figma. See open items for what that tradeoff costs.

## Brand

### Orange — `brand/orange/*`

| Step | Hex |
| --- | --- |
| 50 | `#fff7e8` |
| 100 | `#ffd2ac` |
| 200 | `#ffaa65` |
| 300 | `#ff8400` |
| 400 | `#e16900` |
| 500 | `#bd5500` |
| 600 | `#9a4200` |
| 700 | `#783000` |
| 800 | `#571f00` |
| 900 | `#390e00` |
| 950 | `#1d0200` |

### Deep navy — `brand/deep navy/*`

| Step | Hex |
| --- | --- |
| 50 | `#f5fcff` |
| 100 | `#cfe0ff` |
| 200 | `#abc4ff` |
| 300 | `#8fa9f8` |
| 400 | `#7790dc` |
| 500 | `#6077c2` |
| 600 | `#4a5fa7` |
| 700 | `#35488e` |
| 800 | `#213174` |
| 900 | `#101a5c` |
| 950 | `#04003b` |

## Support

### Red — `red/*`

| Step | Hex |
| --- | --- |
| 50 | `#fef2f2` |
| 100 | `#fee2e2` |
| 200 | `#fecaca` |
| 300 | `#fca5a5` |
| 400 | `#f87171` |
| 500 | `#ef4444` |
| 600 | `#dc2626` |
| 700 | `#b91c1c` |
| 800 | `#991b1b` |
| 900 | `#7f1d1d` |
| 950 | `#450a0a` |

### Yellow — `yellow/*`

| Step | Hex |
| --- | --- |
| 50 | `#fefce8` |
| 100 | `#fef9c3` |
| 200 | `#fef08a` |
| 300 | `#fde047` |
| 400 | `#facc15` |
| 500 | `#eab308` |
| 600 | `#ca8a04` |
| 700 | `#a16207` |
| 800 | `#854d0e` |
| 900 | `#713f12` |
| 950 | `#422006` |

### Green — `green/*`

| Step | Hex |
| --- | --- |
| 50 | `#f0fdf4` |
| 100 | `#dcfce7` |
| 200 | `#bbf7d0` |
| 300 | `#86efac` |
| 400 | `#4ade80` |
| 500 | `#22c55e` |
| 600 | `#16a34a` |
| 700 | `#15803d` |
| 800 | `#166534` |
| 900 | `#14532d` |
| 950 | `#052e16` |

### Teal — `teal/*`

| Step | Hex |
| --- | --- |
| 50 | `#f0fdfa` |
| 100 | `#ccfbf1` |
| 200 | `#99f6e4` |
| 300 | `#5eead4` |
| 400 | `#2dd4bf` |
| 500 | `#14b8a6` |
| 600 | `#0d9488` |
| 700 | `#0f766e` |
| 800 | `#115e59` |
| 900 | `#134e4a` |
| 950 | `#042f2e` |

### Blue — `blue/*`

| Step | Hex |
| --- | --- |
| 50 | `#eff6ff` |
| 100 | `#dbeafe` |
| 200 | `#bfdbfe` |
| 300 | `#93c5fd` |
| 400 | `#60a5fa` |
| 500 | `#3b82f6` |
| 600 | `#2563eb` |
| 700 | `#1d4ed8` |
| 800 | `#1e40af` |
| 900 | `#1e3a8a` |
| 950 | `#172554` |

### Purple — `purple/*`

| Step | Hex |
| --- | --- |
| 50 | `#faf5ff` |
| 100 | `#f3e8ff` |
| 200 | `#e9d5ff` |
| 300 | `#d8b4fe` |
| 400 | `#c084fc` |
| 500 | `#a855f7` |
| 600 | `#9333ea` |
| 700 | `#7e22ce` |
| 800 | `#6b21a8` |
| 900 | `#581c87` |
| 950 | `#3b0764` |

### Neutral — `neutral/*`

| Step | Hex |
| --- | --- |
| 25 | `#fdfdfd` |
| 50 | `#fafafa` |
| 100 | `#f5f5f5` |
| 200 | `#e9eaeb` |
| 300 | `#d5d7da` |
| 400 | `#a4a7ae` |
| 500 | `#717680` |
| 600 | `#535862` |
| 700 | `#414651` |
| 800 | `#252b37` |
| 900 | `#181d27` |
| 950 | `#0a0d12` |

Neutral starts at 25, one step lighter than every other scale's 50.

## Other

### Black and white — `b&w/*`

| Variable | Hex |
| --- | --- |
| `b&w/white` | `#ffffff` |
| `b&w/black` | `#000000` |
| `b&w/transparent` | `#000000`, alpha 0 |

### Alpha dark — `alpha/dark/*`

Black (`#1a1a1a`) at increasing opacity. For dark overlays on light surfaces.

| Step | Opacity |
| --- | --- |
| 50 | 0.06 |
| 100 | 0.09 |
| 200 | 0.20 |
| 300 | 0.28 |
| 400 | 0.36 |
| 500 | 0.48 |
| 600 | 0.60 |
| 700 | 0.70 |
| 800 | 0.75 |
| 900 | 0.80 |
| 1000 | 1.00 |

### Alpha light — `alpha/light/*`

White (`#ffffff`) at increasing opacity. For light overlays on dark surfaces.

| Step | Opacity |
| --- | --- |
| 50 | 0.06 |
| 100 | 0.09 |
| 200 | 0.20 |
| 300 | 0.28 |
| 400 | 0.36 |
| 500 | 0.48 |
| 600 | 0.60 |
| 700 | 0.70 |
| 800 | 0.75 |
| 900 | 0.80 |
| 1000 | 1.00 |

## Open items

- **This is a snapshot, not a sync.** These values were read from Figma on the day this file was written. If a step changes in Figma, this file goes stale until someone updates it by hand — exactly the risk [Colors](colors.md) warns about. If this file is kept, it needs an owner and a habit of re-checking it against Figma, or a generated export instead of a hand-written one.
- **125 raw steps, still no semantic tokens.** This file doesn't change that open item from [Colors](colors.md); it's the same primitives, just with values attached.
- **Alpha steps 800 and 900 are uneven.** Every other step in `alpha/dark` and `alpha/light` moves in a consistent pattern except the jump from 0.60 (600) to 0.70 (700) to 0.75 (800) to 0.80 (900) to 1.00 (1000) — the gaps shrink then jump. Confirm that's intentional.
