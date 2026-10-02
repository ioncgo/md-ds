# Dialog

A dialog is a small window that opens on top of the page and asks the user to decide something before going on. The page behind it is dimmed until the user answers.

## Usage in our case

- **Confirming order actions:** cancel order and delete order. Both can't be undone easily, so we ask first.
- **Not for information:** if nothing needs a decision, don't open a dialog.
- **Not for forms or long content:** those go in a drawer.

## Structure

- **Header:** a title and a close (x) button on the right. The title names the action and the order, like "Cancel order GO-TEST-2026092113-021?".
- **Body:** one short sentence that says what will happen.
- **Footer:** a secondary button and the main action, right aligned. The secondary is on the left.
- **Width:** 408px.

## Variants

| Variant | Main action | Use for |
| --- | --- | --- |
| `default` | Dark blue | Confirming a normal action |
| `destructive` | Red | Deleting, or anything that can't be undone |

- Buttons in the footer are `md`.
- Never use orange in a dialog.

## Closing

- A dialog closes four ways: the x button, the secondary button, the Esc key, and a click outside the dialog.
- All four do the same thing: cancel. Nothing changes, and the order stays as it was.
- Only the main action confirms.
- This is the same for `default` and `destructive`, because closing is always the safe choice.
- When the dialog closes, focus goes back to the button that opened it.
