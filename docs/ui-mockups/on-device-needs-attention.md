# On-Device UI Mock — Needs Attention (v0.1)

**Goal:** Explain the problem clearly without panic. Give the next action.

## Layout (top to bottom)

1) **Header**
- Small turtle icon + “LuckyTurtleMiner”

2) **Status Card (most important)**
- Label: **Status**
- Value: **Needs attention** (red)

3) **Issue Card**
- Label: **Issue**
- Value: short human message, e.g.
  - “Pool auth failed”
  - “DNS / host not found”
  - “No Wi-Fi”
  - “Pool timeout”

4) **Tip Card (simple next step)**
- Label: **Tip**
- Value: one clear action, e.g.
  - “Check username / worker”
  - “Check pool address”
  - “Reconnect Wi-Fi”
  - “Try again in a minute”

5) **Last Attempt Card (optional)**
- Label: **Last try**
- Value: “10s ago” / “1m ago”

6) **Help Card (optional)**
- “Open local web setup to edit settings.”

## Style Notes
- Dark background
- Red accent used lightly (no full red screen)
- Rounded cards, soft spacing
- No flashing/blinking
- Avoid scary wording like “FATAL” or “CRASH”

## When to leave this screen
- If the error clears → return to **Connecting** or **Home/Status**
- If user changes settings → show **Connecting**
