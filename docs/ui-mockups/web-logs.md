# Web UI Mock — Logs Page (v0.1)

**Goal:** Provide recent activity in a readable, calm format.

Logs are for understanding what’s happening, not debugging chaos.

## Layout (top to bottom)

1) **Header**
- Turtle icon + “LuckyTurtleMiner”
- Subtitle: “Activity / Logs”

2) **Controls (small, optional)**
- Button: Copy logs
- Button: Clear view (does not delete device history unless implemented)
- Dropdown: Last 50 / 200 / 500 lines (optional later)

3) **Log Viewer Card**
- Monospace text inside a rounded card
- Dark background, soft contrast
- Each line starts with a short tag:
  - `[WIFI]`
  - `[STRATUM]`
  - `[MINER]`
  - `[UI]`
  - `[ERROR]` (rare)

Example lines:
- `[WIFI] Connected: 192.168.1.42`
- `[STRATUM] Subscribed + authorized`
- `[MINER] Hashrate: 1.02 MH/s`
- `[ERROR] Pool timeout — retrying in 10s`

## Style Notes
- Keep it readable (not tiny)
- No flashing
- Errors highlighted gently (not full red)

## Behavior
- Auto-scroll toggle (on/off)
- New lines append at bottom
- Logs reflect the same “truth” as the Status page
