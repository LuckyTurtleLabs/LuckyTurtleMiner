# LuckyTurtleMiner Architecture (v0.1)

**Status:** Concept + structure (no firmware release yet)  
**Goal:** Define a clean, understandable foundation before implementation begins.

LuckyTurtleMiner is being designed as an **embedded-first miner** focused on ownership, clarity, and long-term reliability.

---

## 1) System Goals

- **Local-first setup** (no accounts, no cloud dependency)
- **Predictable operation** (observable state, simple failure modes)
- **Small surface area** (few moving parts, minimal dependencies)
- **Durable & recoverable** (safe restarts, minimal persistent state)

---

## 2) Core Components

### A. Miner Core
The central loop that:
- receives work
- hashes
- submits results
- maintains basic runtime stats (uptime, accepted/rejected, last share time)

Design intent:
- deterministic behavior
- clear state transitions
- minimal hidden state

---

### B. Work Provider
Where work comes from.

Initial target:
- **Stratum-based pools** (via a lightweight TCP client)

Future possibility:
- optional compatibility with self-hosted infrastructure as the ecosystem grows

---

### C. Network Layer
Responsible for:
- connecting / reconnecting
- timeouts and backoff
- parsing incoming jobs
- sending submissions
- emitting clear error states to the UI/logs

Design intent:
- resilient but simple
- never block the miner core indefinitely

---

### D. Configuration Layer
Holds operator settings such as:
- pool host / port
- user / worker name
- password (if needed)
- device name / branding text
- optional display preferences

Design intent:
- local storage only
- safe defaults
- no “magic” overwrites

---

### E. UI Layer
Two possible surfaces (implementation order TBD):
- **On-device display UI** (status-first)
- **Lightweight local web UI** (setup + status)

Design intent:
- clarity > decoration
- show the few metrics that matter
- make failures obvious

---

### F. Persistence Layer
Stores only what’s required:
- configuration values
- optional last-known state (non-critical)

Design intent:
- survive power loss safely
- easy “factory reset”
- no fragile database

---

## 3) Data Flow (Concept)

     +--------------------+
     |   UI Layer         |
     | (Display/Web)      |
     +---------+----------+
               |
               v
+------------------+------------------+
| Shared Runtime State |
| (stats, connection, errors, config) |
+------------------+------------------+
|
v
+----------+----------+
| Miner Core |
| (hash/submit/stats) |
+----------+----------+
|
v
+----------+----------+
| Network Layer |
| (stratum comms) |
+----------+----------+
|
v
+----------+----------+
| Work Provider |
| (pool / node) |
+---------------------+


---

## 4) Runtime State (Minimal)

At minimum, the system should expose:

- Connection state: `disconnected | connecting | subscribed | authorized | active`
- Pool info: host/port
- Hashrate (rolling estimate)
- Shares: accepted / rejected
- Uptime
- Last share timestamp
- Last error (human readable)

---

## 5) Failure Modes (First-Class)

LuckyTurtleMiner should treat these as normal events:

- Wi-Fi / network drop
- Pool unreachable / timeout
- Authorization failure
- Invalid job / parse error
- Low memory / watchdog risk

Design intent:
- show clear status
- attempt recovery with backoff
- never “hang silently”

---

## 6) Non-Goals (For v0.x)

To keep early versions sane, v0.x will avoid:

- complex dashboards
- remote cloud control
- automatic “smart tuning”
- performance claims without measurement
- sprawling dependency chains

---

## 7) Next Architecture Additions (Future)

These are intentionally deferred until the foundation is stable:

- hardware target matrix (which ESP32 variants / displays)
- UI screen map (what screens exist and what they show)
- config schema definition (exact keys + validation rules)
- logging strategy (serial vs local web vs file)
- testing strategy (simulation, test pools, etc.)

---

## 8) Notes

This document is meant to evolve.  
When implementation starts, changes will be expected, but the **principles** remain: ownership, clarity, durability.

🐢

