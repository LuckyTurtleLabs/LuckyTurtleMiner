# Web UI Mock — Status Page (v0.1)

**Goal:** Show the same truth as the device screen, just bigger and clearer.

This page is read-only.

## Layout (top to bottom)

1) **Header**
- Turtle icon + “LuckyTurtleMiner”
- Subtext: device name (optional)

2) **Overall Status Card**
- Status: **Hashing ✓** (green)
- Pool: `pool.example.com`
- IP: `192.168.1.42`
- Uptime: `03:41:22`

3) **Performance Card**
- Speed: `1.02 MH/s`
- Shares:
  - Accepted: `12`
  - Rejected: `0`
- Last share: `20s ago`

4) **Connection Card**
- State: connected
- Last reconnect: `—`
- Errors: none

## Style Notes
- Dark background
- Rounded cards
- Turtle green accent for healthy state
- Large readable numbers
- No charts unless added later for a reason

## Behavior
- Auto-refresh (simple interval)
- No user interaction on this page
