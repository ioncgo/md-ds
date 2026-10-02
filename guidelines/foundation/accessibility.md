# Accessibility and color contrast

This file sets the contrast and color rules for the design system. It is written for designers, developers and AI tools that generate or review UI.

How to read it:

- Rules marked **MUST** or **NEVER** are hard rules. No exceptions without a written sign-off.
- Every hard rule has an ID (for example `A11Y-03`). Use the ID when you flag a problem in review.
- Colors are named by variable, as in [Colors](colors.md). Hex values are not written here. The Figma variables are the source of truth.

## The standard

We build to WCAG 2.2 AA, which contains all of WCAG 2.1 AA. The EU's legal reference (EN 301 549) still points at 2.1 today, but its September 2026 update points at 2.2, so 2.2 is where this is heading.

AAA is out of scope. Rules below marked "our rule" are stricter than WCAG and are ours, not law.

## Contrast thresholds

| What | Minimum contrast | WCAG rule |
| --- | --- | --- |
| Body text, labels, button text, placeholder text | 4.5:1 | 1.4.3 |
| Large text (24px regular, or 18.66px bold and up) | 3:1 | 1.4.3 |
| UI parts people need to see (borders, icons, focus rings, chart lines) | 3:1 against what's next to them | 1.4.11 |

The dashboard is read on warehouse floors, often on shared screens and from a few steps away. Treat these numbers as the floor, not the goal.

## Brand color tokens

| Token | Role |
| --- | --- |
| `brand/orange/300` | Brand orange. Never a button fill. |
| `brand/orange/400` | Primary button, default |
| `brand/orange/500` | Primary button, hover |
| `brand/orange/600` | Primary button, pressed |
| `brand/deep navy/950` | Dark button, default |
| `brand/deep navy/900` | Dark button, hover |
| `brand/deep navy/700` | Dark button, pressed |
| `blue/600` | Links |
| `blue/800` | Links, hover |
| `red/600` | Destructive button |
| `red/700` | Error text, destructive hover |
| `text/default` | Main text color. Not in Figma yet. Today this is `neutral/950`. |
| `neutral/600` | Secondary text, outlined button label |

## Problem 1: orange can't carry white text

`brand/orange/400` with white text is 3.38:1. That passes for large text but fails the 4.5:1 that 14px button labels need. `brand/orange/300` is worse at 2.46:1.

Going darker fixes the number and breaks the brand. `brand/orange/500` passes at 4.71:1, but it reads as burnt, and it sits 1.03:1 from the destructive red. At that point a primary button and a delete button look the same to anyone who can't separate the hues.

| Token | White text | Where it's used |
| --- | --- | --- |
| `brand/orange/300` | 2.46:1, fails | Brand only |
| `brand/orange/400` | 3.38:1, fails | Primary button, default. Logged exception (EX-01). |
| `brand/orange/500` | 4.71:1, passes | Primary button, hover |
| `brand/orange/600` | 6.66:1, passes | Primary button, pressed |

**Decision.** We ship white on `brand/orange/400` and log it as an exception, so the primary button stays on brand. Only the resting state falls short. See EX-01 at the end of this file.

## Problem 2: deep navy looks like dark gray

Deep navy passes easily with white text on every dark step, so contrast is not the issue. The issue is that the dark steps sit almost on top of the dark text neutral, so the eye reads "dark", not "blue".

That means deep navy can't mark links or selected states. Those use `blue/600` instead, which is 5.17:1 on white and 3.76:1 against body text, so it clears 1.4.1 on color alone.

## Hard rules

### Text and contrast

- **A11Y-01.** MUST meet the thresholds in the table above for every text and UI color pair, in light and dark mode.
- **A11Y-02.** NEVER use opacity or transparency to make text lighter. Use a solid color token. Contrast checkers often miss faded text, and it looks different on every background.
- **A11Y-03.** MUST meet 4.5:1 for placeholder text and helper text. They are text, not decoration.
- **A11Y-04.** NEVER set text below 12px. Body text on dashboards starts at 14px. (Our rule, stricter than WCAG.)
- **A11Y-05.** MUST recheck contrast when text sits on anything other than a flat color (images, gradients, chart areas, striped table rows).

### Orange

- **A11Y-06.** White text on orange is allowed on the filled primary button only, and only because of EX-01. NEVER put white on orange anywhere else.
- **A11Y-07.** NEVER use orange on outlined or text buttons. Orange is a fill color only.
- **A11Y-08.** MUST take hover and pressed darker, to `brand/orange/500` (4.71:1) and `brand/orange/600` (6.66:1). Both pass with white text.
- **A11Y-09.** NEVER use orange for body text or labels on white. `brand/orange/400` on white is 3.38:1.
- **A11Y-10.** Orange is allowed for icons, borders and focus rings as long as it hits 3:1. `brand/orange/400` does at 3.38:1. `brand/orange/300` does not at 2.46:1.
- **A11Y-11.** NEVER use orange as a status color. Status has its own color set.
- **A11Y-12.** NEVER let a primary button and a destructive button be told apart by color alone. `brand/orange/500` and `red/600` are 1.03:1 apart in brightness. Separate them by label and position.

### Deep navy, blue and neutrals

- **A11Y-13.** Deep navy's one job is the dark button: `brand/deep navy/950` default, `brand/deep navy/900` hover, `brand/deep navy/700` pressed, white text throughout. NEVER use it for links or selected states.
- **A11Y-14.** MUST use `blue/600` for links and `blue/800` on hover.
- **A11Y-15.** MUST keep the dark text neutral a true gray with very little blue in it, so it doesn't blend with navy.
- **A11Y-16.** MUST make a visited link tell itself apart from body text by more than hue. `brand/orange/800` at 1.48:1 against body text does not.

### Status and state

- **A11Y-17.** NEVER show status with color alone. Every status chip has a text label, and critical states also get an icon.
- **A11Y-18.** NEVER show selected or active states with color alone. Add a second cue: check mark, bold weight, underline or filled background.
- **A11Y-19.** Charts MUST NOT rely on color alone to tell series apart. Use direct labels, line styles or patterns.

### Focus and interaction

- **A11Y-20.** MUST show a visible focus ring on every interactive element: at least 2px, and at least 3:1 against the colors on both sides of it.
- **A11Y-21.** NEVER remove the focus outline without replacing it with one that meets A11Y-20.
- **A11Y-22.** NEVER put information people need only in a hover tooltip. Floor screens are often touch or shared, and hover doesn't exist there.
- **A11Y-23.** MUST give every drag interaction a click-only path too. Reordering or resizing columns can't be drag-only (2.5.7).
- **A11Y-24.** NEVER leave a focused row or cell fully hidden behind a sticky header or footer. Scroll it into view when focus lands on it (2.4.11).
- **A11Y-25.** MUST make clickable targets at least 24×24px on desktop and 44×44px on touch screens, even when the icon inside is smaller (2.5.8).
- **A11Y-26.** MUST give icon-only buttons an accessible name.

## Review checklist

Use this when reviewing a screen or component, by hand or with an AI tool. Each line maps to a rule.

- [ ] All text pairs pass 4.5:1, large text 3:1 (A11Y-01, A11Y-03)
- [ ] No faded text made with opacity (A11Y-02)
- [ ] No text under 12px, body text 14px or more (A11Y-04)
- [ ] White on orange appears only on the filled primary button (A11Y-06)
- [ ] No orange on outlined buttons, body text or status (A11Y-07, A11Y-09, A11Y-11)
- [ ] Primary and destructive buttons differ by more than color (A11Y-12)
- [ ] Deep navy is not used for links or selected states (A11Y-13)
- [ ] Links use `blue/600`, and visited links are distinguishable from body text (A11Y-14, A11Y-16)
- [ ] Status chips have labels, critical ones have icons (A11Y-17)
- [ ] Selected states have a cue besides color (A11Y-18)
- [ ] Chart series can be told apart without color (A11Y-19)
- [ ] Focus ring visible on every interactive element (A11Y-20, A11Y-21)
- [ ] Nothing important hidden behind hover (A11Y-22)
- [ ] Every drag action has a click-only path (A11Y-23)
- [ ] Focused rows not hidden behind sticky headers (A11Y-24)
- [ ] Targets meet 24px desktop or 44px touch (A11Y-25)
- [ ] Icon-only buttons have accessible names (A11Y-26)

## Exceptions

One exception is open. Everything else in this file is a rule with no exceptions.

**EX-01. White text on the `brand/orange/400` primary button.**

- **What it breaks.** WCAG 1.4.3. White on `brand/orange/400` is 3.38:1, against the 4.5:1 that 14px labels need.
- **Why we're keeping it.** The primary button stays on brand. Every orange dark enough to pass white text reads as red, and red already means error in this product.
- **How far it goes.** The resting state of the filled primary button, and nothing else. Hover (4.71:1) and pressed (6.66:1) both pass. No other component may put white on orange.
- **What we do about it.** The button is never the only path to an action, and on screens read at a distance or in bright light we use the dark navy button instead.
- **When to revisit.** If the brand orange changes, and before any conformance report goes to a customer, since an open exception has to be declared there.
