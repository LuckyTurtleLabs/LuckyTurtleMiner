# LuckyTurtleMiner UI Data (Minimal) — v0.1

This document defines the **minimum runtime data** required to render the UI mockups.
No extra metrics. No future features. Just what the UI needs.

---

## On-Device: Home / Status Screen

### Required fields
- **device_name** (string)
  - Example: `LuckyTurtle-01`

- **status** (enum)
  - Values: `hashing` | `connecting` | `needs_attention`
  - Example: `hashing`

- **pool_host** (string)
  - Example: `pool.example.com`

- **hashrate** (number)
  - Meaning: current rolling hashrate
  - Example: `1.02`

- **hashrate_unit** (enum)
  - Values: `H/s` | `kH/s` | `MH/s` | `GH/s` | `TH/s`
  - Example: `MH/s`

- **shares_accepted** (integer)
  - Example: `12`

- **shares_rejected** (integer)
  - Example: `0`

- **uptime_seconds** (integer)
  - Example: `13282`

### Derived (UI formatting only)
These are calculated in the UI, not stored as separate fields:
- **uptime_display** (e.g., `03:41:22`) derived from `uptime_seconds`
- **shares_display** (e.g., `12 accepted · 0 rejected`) derived from share counts
- **status_label/color**
  - `hashing` → green
  - `connecting` → yellow
  - `needs_attention` → red

---
