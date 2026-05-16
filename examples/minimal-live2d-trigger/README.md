# Minimal Live2D Trigger

This example placeholder shows the core idea behind driving a browser avatar from a backend process.

## Flow

```text
AI audio generated
      |
      v
calculate mouth-open values
      |
      v
send JSON over websocket
      |
      v
browser source applies value to avatar mouth parameter
```

## Example websocket payload

```json
{
  "mouthOpenY": [0.1, 0.4, 0.8, 0.3, 0.0],
  "windowMs": 50
}
```

## Design notes

- Keep the browser renderer separate from the AI voice runtime.
- Smooth mouth values in the browser.
- Fail visibly if the websocket disconnects.
