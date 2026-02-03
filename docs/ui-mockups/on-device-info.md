# On-Device UI Mock — Info (v0.1)

**Goal:** Show basic device info and help the operator identify the miner.

## Layout (top to bottom)

1) **Header**
- Small turtle icon + “LuckyTurtleMiner”

2) **Device Card**
- Label: **Device**
- Value: device name (e.g. `LuckyTurtle-01`)

3) **IP Card**
- Label: **IP Address**
- Value: `192.168.1.42`

4) **Version Card**
- Label: **Firmware**
- Value: `v0.1 (architecture phase)`

5) **Uptime Card**
- Label: **Uptime**
- Value: `03:41:22`

6) **Hint Card (small text)**
- “Open local web UI for setup and logs.”

## Style Notes
- Dark background
- Neutral accent (green or muted blue)
- Rounded cards, soft spacing
- No alerts or warnings on this screen

## When to show this screen
- User taps a button
- User cycles screens
- Used mainly for identification and support
