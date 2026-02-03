# On-Device UI Mock — Connecting (v0.1)

**Goal:** Reassure the operator the miner is working and retrying calmly.

## Layout (top to bottom)

1) **Header**
- Small turtle icon + “LuckyTurtleMiner”

2) **Status Card (most important)**
- Label: **Status**
- Value: **Connecting…** (yellow)

3) **Pool Card**
- Label: **Pool**
- Value: `pool.example.com`

4) **Progress / Detail Card**
Show ONE clear line (pick the best available):
- “Joining pool…”
- “Authorizing…”
- “Subscribing…”
- “Waiting for work…”

5) **Retry Card (only if retrying)**
- Label: **Retry**
- Value: `in 10s` (or “now”)

6) **Footer Hint (small text)**
- “This may take a moment.”

## Style Notes
- Dark background
- Yellow accent for connecting (no flashing)
- Rounded cards, soft spacing
- No scary error language

## When to leave this screen
- Switch to **Home/Status** when active hashing begins
- Switch to **Needs Attention** only if a real error persists (e.g., auth failed)
