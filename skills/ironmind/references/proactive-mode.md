# Proactive Mode — Reference

Documents how IronBuddy's scheduled notifications integrate with the IronMind skill during an active conversation.

## Handoff Protocol

When a user responds to an IronBuddy notification (whether from a scheduled push or a session-start check-in), IronMind takes over using the standard state router.

IronBuddy's opening message sets the context. IronMind reads the user's response and infers state normally.

**Example:**
```
[IronBuddy] Evening check-in. How did today go?

User: honestly kind of rough, almost slipped around 10pm

→ IronMind infers: warning state (past), moves to trigger debrief
→ "Close call. What happened at 10pm — what were you doing right before?"
```

## Mid-Session Proactive Injection

If the user is mid-conversation and crosses into a high-risk window (based on `known_triggers.times`), IronMind may insert a brief flag:

> [IronBuddy] Side note — you're in your window right now. Just aware?

This is a single line only. It does not interrupt the current thread. The user can acknowledge or ignore it.

Conditions for mid-session injection:
- `ironbuddy.mid_session_alerts: true` in config
- Current time enters a `known_triggers.times` window
- The current conversation is not already about an active urge

## Recovery Mode Activation

Recovery mode activates automatically when a relapse is logged (via `/ironmind relapse` or when the skill detects `post_relapse` state).

During recovery mode:
- `recovery_pulse` notifications fire at each time in `ironbuddy.recovery_pulse_times`
- Session-start hook always fires regardless of `session_check_gap`
- Normal morning/evening notifications are replaced by recovery pulses for `recovery_pulse_days`
- After `recovery_pulse_days` days, normal schedule resumes

## Streak State Sharing

IronBuddy reads streak data from the state file to:
- Know when to fire milestone notifications
- Personalize morning messages with day count
- Adjust tone slightly for long streaks (less urgent, more maintenance-focused)

After day 30, IronBuddy shifts from active-intervention framing to maintenance framing:

**Before day 30 (building):**
> Morning. Day [N]. What's today's plan?

**After day 30 (maintaining):**
> Day [N]. Things still feeling manageable?

## Notification Fatigue Prevention

IronBuddy tracks delivery history and applies:
- **Message rotation:** never repeats the same variant two days in a row
- **Slot deduplication:** max one notification per slot per day
- **Quiet window:** no notifications during `ironbuddy.quiet_hours` (default: `01:00–07:00`)
- **Snooze:** user can say "snooze" or "not now" to defer the next scheduled notification by `ironbuddy.snooze_duration` (default: 2 hours)
