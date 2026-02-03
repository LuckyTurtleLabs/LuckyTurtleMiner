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
## On-Device: Connecting Screen

### Required fields
- **device_name** (string)

- **status** (enum)
  - Must be `connecting` while on this screen

- **pool_host** (string)

- **connect_phase** (enum)
  - Values: `wifi` | `dns` | `tcp` | `subscribing` | `authorizing` | `waiting_for_work`
  - Example: `authorizing`

- **retry_in_seconds** (integer, optional)
  - Only present if currently retrying
  - Example: `10`

### Derived (UI formatting only)
- **phase_label**
  - `wifi` → “Connecting Wi-Fi…”
  - `dns` → “Resolving host…”
  - `tcp` → “Opening connection…”
  - `subscribing` → “Joining pool…”
  - `authorizing` → “Authorizing…”
  - `waiting_for_work` → “Waiting for work…”
- **retry_display**
  - Example: “Retrying in 10s” derived from `retry_in_seconds`

## On-Device: Needs Attention Screen

### Required fields
- **device_name** (string)

- **status** (enum)
  - Must be `attention`

- **issue_type** (enum)
  - Values:
    - `wifi_failed`
    - `pool_unreachable`
    - `auth_failed`
    - `low_memory`
    - `overheat`
    - `unknown`

- **short_message** (string)
  - Friendly, one-line explanation
  - Example: “Can’t reach the pool right now”

### Optional fields
- **details** (string)
  - Human-readable detail for advanced users
  - Example: “Connection timed out after 10 seconds”

- **suggested_action** (string)
  - Example:
    - “Check Wi-Fi settings”
    - “Verify pool address”
    - “Let the device cool down”

- **retry_available** (boolean)
  - If true, UI shows “Retrying automatically”

- **retry_in_seconds** (integer, optional)

### Derived (UI formatting only)
- **icon_hint**
  - `wifi_failed` → Wi-Fi icon
  - `pool_unreachable` → Link/broken-chain icon
  - `auth_failed` → Key icon
  - `overheat` → Thermometer icon
  - `unknown` → Turtle shrug 🙂

## On-Device: Info / Status Screen

### Required fields
- **device_name** (string)

- **status** (enum)
  - Must be `mining`

- **uptime_seconds** (integer)
  - Example: `8640`

- **hashrate_hs** (number)
  - Hashrate in H/s
  - Example: `1200000`

- **accepted_shares** (integer)

### Optional fields
- **rejected_shares** (integer)
  - Omit if zero to reduce clutter

- **pool_host** (string)

- **last_share_seconds_ago** (integer)
  - Example: `42`

- **temperature_c** (number, optional)
  - Only shown if sensor exists

### Derived (UI formatting only)
- **hashrate_display**
  - Example: “1.2 MH/s”

- **uptime_display**
  - Example: “2h 24m”

- **share_status**
  - If `last_share_seconds_ago < 120` → “Active”
  - Else → “Waiting for work”

- **health_indicator**
  - Green if no issues
  - Yellow if `rejected_shares > 0`
 
    ## Web UI: Status Page (Minimal)

The web Status page shows the same truth as on-device, plus IP for convenience.

### Required fields
- **device_name** (string)
- **status** (enum)
  - Values: `mining` | `connecting` | `attention`

- **pool_host** (string)

- **ip_address** (string)
  - Example: `192.168.1.42`

- **uptime_seconds** (integer)

- **hashrate_hs** (number)

- **accepted_shares** (integer)
- **rejected_shares** (integer)

### Optional fields
- **last_share_seconds_ago** (integer)

- **last_error_message** (string)
  - Only present if status = `attention`

### Derived (UI formatting only)
- **hashrate_display** (auto scales H/s → kH/s → MH/s etc.)
- **uptime_display**
- **status_badge_color**

## Web UI: Setup Page (Minimal)

The Setup page allows configuring network-independent mining settings.

### Required fields
- **device_name** (string)
  - Editable
  - Example: “LuckyTurtle-01”

- **pool_host** (string)
  - Example: `stratum.example.com`

- **pool_port** (integer)
  - Example: `3333`

- **wallet_address** (string)

### Optional fields
- **worker_name** (string)
  - Example: `turtle01`

- **use_tls** (boolean)
  - Default: false

- **save_pending** (boolean)
  - True while settings are not yet applied

### Actions (UI-triggered)
- **save_config**
- **reboot_device**

### Derived (UI formatting only)
- **pool_display**
  - Example: `stratum.example.com:3333`

## Web UI: Logs Page (Minimal)

Logs are a simple recent-activity feed.

### Required fields
- **log_lines** (array of strings)
  - Each line is already formatted for display
  - Examples:
    - `[WIFI] Connected: 192.168.1.42`
    - `[STRATUM] Subscribed + authorized`
    - `[MINER] Hashrate: 1.02 MH/s`
    - `[ERROR] Pool timeout — retrying in 10s`

### Optional fields
- **log_max_lines** (integer)
  - Example: `200`

- **log_updated_seconds_ago** (integer)
  - Example: `1`

### Derived (UI formatting only)
- UI may display timestamps later, but v0.1 does not require them
