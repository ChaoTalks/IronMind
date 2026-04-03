---
name: schedule
event: Schedule
description: "Cron-based scheduled notifications. Fires IronBuddy messages at configured times independent of whether the user has an active session. Supports morning check-in, pre-window alert, evening wind-down, milestone, silence alarm, and post-relapse recovery pulse."
---

# Hook: Schedule (`Schedule`)

Runs on a cron-like schedule defined in `config.yaml` under `ironbuddy`. Sends proactive IronBuddy notifications to the user outside of active sessions.

## Schedule Slots

| Slot | Config Key | Default | Notification Type |
|---|---|---|---|
| Morning | `ironbuddy.morning_time` | `08:00` | `morning` |
| Pre-window | auto-derived from `known_triggers.times` | 30 min before | `pre_window` |
| Evening | `ironbuddy.evening_time` | `21:30` | `evening` |
| Silence check | daily at `ironbuddy.morning_time` | — | `silence` (conditional) |
| Recovery pulse | `ironbuddy.recovery_pulse_times` | `["09:00","21:00"]` | `recovery_pulse` |

Milestone notifications (`milestone`) are sent at `ironbuddy.morning_time` on milestone days, merged with the morning message.

## Execution Order

For each scheduled slot:

1. Load state: streak count, last check-in timestamp, last relapse timestamp, recovery mode flag
2. Run IronBuddy decision logic (see `agents/ironbuddy.md`)
3. Select and render the appropriate message variant
4. Deliver via configured `ironbuddy.delivery` channel
5. Write delivery timestamp to state

## Delivery Channels

Configured under `ironbuddy.delivery` in `config.yaml`:

| Channel | Description |
|---|---|
| `openclaw` | Native openclaw notification (default) |
| `system` | OS-level desktop notification |
| `both` | openclaw + system notification |

## Deduplication

The scheduler will not send the same notification type more than once per calendar day, except:
- `recovery_pulse` — sends at each configured time during recovery window
- `pre_window` — sends once per high-risk window entry per day

## Disabling

Set `ironbuddy.schedule: false` in `config.yaml` to disable all scheduled notifications. Individual slots can be disabled by setting their time to `null`.
