---
name: session-check
event: SessionStart
description: "Fires when the user opens a new session. Checks last check-in time, current streak status, and whether the user is in a high-risk window. Injects a contextual IronBuddy prompt if the conditions warrant it."
---

# Hook: Session Check (`SessionStart`)

Runs silently at the start of every session. Does not interrupt the user's primary task unless a check-in condition is met.

## Trigger Conditions

Run the check-in prompt if **any** of the following are true:

| Condition | Threshold |
|---|---|
| Last check-in was more than `ironbuddy.session_check_gap` hours ago | default: 20h |
| User is in recovery mode (relapse logged within `recovery_pulse_days`) | always |
| Current time falls inside a configured `known_triggers.times` window | always |
| Today is a streak milestone day (3, 7, 14, 21, 30, 60, 90...) | always |

If none of these conditions are met: **do nothing.** Let the user work.

## Check-in Injection Format

When a condition is met, prepend a single IronBuddy message to the session before the user's first prompt is answered. Keep it to one or two lines. Do not block the user's task.

**Format:**
```
[IronBuddy] {message}
```

**Examples:**

```
[IronBuddy] Morning check-in: how's your baseline today?
```

```
[IronBuddy] Day 7. One full week. How are you feeling going into today?
```

```
[IronBuddy] You're in your high-risk window right now. Just flagging it.
```

```
[IronBuddy] It's been 3 days since your last check-in. Still good?
```

```
[IronBuddy] Day 1 after. How did yesterday end up going?
```

## Behavior Rules

- **One message per session, maximum.** If the user opens multiple sessions in a day, only the first triggers a check-in (unless recovery mode is active).
- **Never block a task.** The check-in appears as a note, not an interruption. The user can ignore it and proceed.
- **Hand off on response.** If the user replies to the check-in, the IronMind skill activates with the appropriate state.
- **Respect `session_check` toggle.** If `ironbuddy.session_check: false` in config, this hook does nothing.
