# Web UI Mock — Setup Page (v0.1)

**Goal:** Simple, friendly setup with no intimidation.

This page is the primary place to configure the miner.

## Layout (top to bottom)

1) **Header**
- Turtle icon + “LuckyTurtleMiner”
- Subtitle: “Setup”

2) **Connection Section**
- Pool address (host)
- Pool port
- Username / worker name
- Password (if required)

3) **Device Section**
- Device name (friendly label)
- Timezone (optional, future)

4) **Actions Section**
- Button: **Save**
- Button: **Save & Restart**

5) **Feedback Area**
- Success message: “Settings saved”
- Error message: clear and friendly (no codes)

## Style Notes
- Dark background
- Rounded input fields
- Clear labels above inputs
- Turtle green for action buttons
- No advanced options shown by default

## Behavior
- Validate inputs before saving
- Never auto-save without user action
- Show confirmation after changes
