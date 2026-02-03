# On-Device UI Mock — Home / Status (v0.1)

**Goal:** Show the miner is healthy at a glance (friendly turtle club feel).

## Layout (top to bottom)

1) **Header**
- Small turtle icon + “LuckyTurtleMiner”
- Subtext: device name (optional later)

2) **Status Card (most important)**
- Label: **Status**
- Value: **Hashing ✓** (green)

3) **Pool Card**
- Label: **Pool**
- Value: `pool.example.com`

4) **Speed Card**
- Label: **Speed**
- Value: `1.02 MH/s` (or GH/s depending)

5) **Shares Card**
- Label: **Shares**
- Value: `12 accepted · 0 rejected`

6) **Uptime Card**
- Label: **Uptime**
- Value: `03:41:22`

## Style Notes
- Dark background
- Turtle green accent (#36d27a) for “good” state
- Rounded cards, soft spacing
- Large readable numbers
- No flashing/blinking

## When to leave this screen
- Stay here during normal operation
- Switch only if:
  - connecting/reconnecting
  - needs attention (error)
