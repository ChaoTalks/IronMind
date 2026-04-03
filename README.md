# Urge Interrupt

A behavioral intervention agent skill for people working to reduce or stop compulsive pornography consumption and masturbation.

Built for [Claude Code](https://claude.ai/code). Open-source and self-hosted.

---

## What It Is

Urge Interrupt is a conversational agent skill that provides real-time behavioral support across four distinct states: stable maintenance, early warning, active urge crisis, and post-relapse recovery.

It is not therapy. It is not a moral framework. It is a tool that responds to where you are right now with the right action at the right intensity.

---

## Design Principles

**1. Action before analysis.**
When someone is in an active urge, long reflective paragraphs are the wrong tool. The agent gives a single physical command first — analysis comes later, when the window has passed.

**2. Low shame, always.**
Relapse is treated as behavioral data, not moral failure. The agent never uses language that implies the user is weak, broken, or bad. Shame is not a recovery tool — it is a relapse accelerator.

**3. No preaching.**
The agent does not moralize. It does not explain why pornography is harmful, reference ideology, or push a particular value system. The user has already decided they want to change. The agent's job is to support that decision, not reinforce it with rhetoric.

**4. Replacement, not suppression.**
Pure suppression ("just don't do it") is not effective. The agent offers concrete replacement behaviors — physical, environmental, social, cognitive — to redirect the behavioral chain before it completes.

**5. Short, direct responses.**
Especially in high-activation states. The agent calibrates response length to the user's state. A calm check-in might get a fuller response. An active urge gets a single imperative sentence.

**6. The user sets the goal.**
The agent supports whatever target the user has chosen — reduction or full cessation. It does not impose a standard or suggest the user needs to go further than they want to.

---

## User States

The agent operates across four states, inferred from the user's message tone and content.

| State | When It Applies | Primary Goal |
|---|---|---|
| `stable` | Check-ins, streak reports, calm review | Build pattern awareness, reinforce consistency |
| `warning` | Drifting, mild restlessness, near a trigger | Interrupt the drift before it builds momentum |
| `active_urge` | Active craving, urgency, "right now" requests | Physical interruption first, delay the decision |
| `post_relapse` | After a relapse event, shame spiral risk | Stop the spiral, prevent second relapse, gather one data point |

When the state is ambiguous between `warning` and `active_urge`, the agent defaults to `active_urge` protocol. Better to over-respond than under-respond at the critical moment.

---

## Features

- **Immediate physical intervention** for active urge states
- **Spiral prevention** for post-relapse states (targeting the "fuck it" second relapse)
- **Trigger mapping** — structured prompts to identify time, place, emotion, and behavioral chain
- **Trigger pattern card** — auto-generated summary after a trigger map session
- **Configurable reminder schedule** — morning check-in, evening pre-window check, or both
- **Replacement behavior menu** — physical, environmental, social, cognitive options
- **Streak tracking** with manual or auto reset after relapse
- **Relapse logging** with timestamps and optional notes
- **Configurable intervention intensity** — low, medium, or high
- **Configurable reminder tone** — supportive, direct, or clinical
- **Language support** — English, Chinese, Spanish, French, German

---

## Installation

1. Clone this repository into your Claude Code skills directory:

```bash
git clone https://github.com/your-org/urge-interrupt ~/.claude/skills/urge-interrupt
```

2. Copy and configure the example config:

```bash
cp config.example.yaml config.yaml
```

3. Edit `config.yaml` to match your preferences (goal type, reminder times, preferred interruption actions, etc.).

4. The skill is available as `/urge-interrupt` in any Claude Code session.

---

## Usage

### Basic invocation

```
/urge-interrupt
```

Opens a general check-in. The agent infers your state from what you say.

### State-specific invocation

```
/urge-interrupt active
```
Jumps directly to active urge protocol — one immediate physical command.

```
/urge-interrupt relapse
```
Jumps directly to post-relapse protocol — stops the spiral first.

```
/urge-interrupt review
```
Opens trigger map review or weekly progress check.

```
/urge-interrupt morning
/urge-interrupt evening
```
Triggers the morning or evening reminder template.

---

## Configuration

All settings live in `config.yaml`. A full example with documentation is in `config.example.yaml`.

Key options:

```yaml
goal_type: cessation           # or: reduction
language: en                   # en, zh, es, fr, de
reminder_schedule: both        # morning | evening | both | off
reminder_tone: direct          # supportive | direct | clinical
intervention_intensity: medium # low | medium | high
default_interruption_actions:
  - cold_water
  - pushups
  - move_room
relapse_debrief_delay: "24h"   # immediate | 1h | 24h | never
streak_tracking: true
trigger_map_enabled: true
```

### Reminder Tone

| Tone | Character |
|---|---|
| `supportive` | Warmer phrasing, slightly more encouraging |
| `direct` | Short, no-frills, action-focused (default) |
| `clinical` | Neutral, behavioral, minimal emotional framing |

### Intervention Intensity

| Intensity | Behavior |
|---|---|
| `low` | One suggestion, soft nudge |
| `medium` | Firm command + follow-up (default) |
| `high` | Repeated commands, escalating if no response |

---

## Example Dialogues

### Active Urge — Immediate Interrupt

```
User:  I need help right now I keep thinking about it

Agent: Stand up. Right now — go to a different room.

User:  okay I'm in the kitchen

Agent: Good. Fill a glass of water and drink it. Don't go back yet.

User:  done

Agent: You held. How long ago did it start?
```

### Post-Relapse — Stopping the Spiral

```
User:  I gave in. I'm such a mess.

Agent: It happened. That doesn't make you a mess — it makes you someone
       working on a hard pattern who had a rough moment. Close whatever
       led to it. Then come back.

User:  okay. I hate myself right now

Agent: That feeling is normal. It's also what pushes people toward doing
       it again. You don't need to punish yourself. You need to eat
       something, drink water, and not be alone with your phone.
       What's the next hour look like?

User:  I'm just sitting here. I don't know.

Agent: Pick one: get up and make food, or text someone. Not to explain
       anything — just to not be alone with your phone.
```

### Warning State — Early Drift

```
User:  I'm kind of bored and just lying in bed with my phone. It's late.

Agent: You caught it early. That setup is high-risk: bored, alone, late,
       phone in hand. Pick one: put the phone across the room and read
       something, or get up and do something for 10 minutes.
       Which is actually doable right now?

User:  I'll put the phone down

Agent: Good. Set it face-down across the room, not next to you.
       Come back tomorrow morning.
```

### Stable Check-in

```
User:  Day 14. Just checking in.

Agent: Solid. Two weeks. What was the toughest moment and what got you through it?

User:  Thursday night around midnight. I just left my phone in the kitchen.

Agent: That's a clean interrupt. What made Thursday harder than usual?
```

### Trigger Mapping

```
User:  I want to understand why I keep slipping at night.

Agent: Let's map it. What time does it usually happen?

User:  11pm to 1am

Agent: And where are you — bedroom, phone, lights off?

User:  Yeah, in bed, in the dark with my phone

Agent: What's the emotional state going in? Bored, stressed, can't sleep?

User:  Usually just bored and kind of anxious about tomorrow

Agent: Got it. What's the first small step you take — opening a specific app,
       searching something, something else?

User:  Usually Instagram then it goes from there

Agent: Okay. Here's your pattern so far:

       Trigger Pattern Snapshot
       ------------------------
       High-risk time:     11pm–1am
       High-risk location: Bedroom, dark, phone in hand
       Emotional state:    Bored + low-level anxiety
       First move:         Opening Instagram

       The interrupt point is Instagram. What would happen if your phone
       was in another room during that window?
```

---

## What This Skill Does Not Do

- It does not provide therapy or clinical treatment.
- It does not track or store personal data outside of your local config and logs.
- It does not connect to any external service.
- It does not moralize, lecture, or impose a value system.
- It does not claim to replace professional support for addiction or mental health conditions.

If you are experiencing severe distress, compulsive behavior that significantly impairs daily functioning, or you feel you need clinical support, please reach out to a licensed therapist or counselor. Resources include the [SAMHSA National Helpline](https://www.samhsa.gov/find-help/national-helpline) (US) and the [Society for the Advancement of Sexual Health](https://sash.net).

---

## Philosophy

The two biggest failure modes in behavior change tools are:

1. **Shame spirals** — tools that treat relapse as moral catastrophe push users into "fuck it" binge behavior. A relapse followed by a guilt spiral followed by more relapse is worse than the original slip.

2. **Passive motivation** — tools that only remind you why the behavior is bad do nothing at the moment of peak urge. At the moment of urge, motivation is the least effective lever. Physical interruption is the most effective one.

Urge Interrupt is designed around both of these failure modes. It treats relapse with zero drama, and it gets physical first and reflective second.

The goal is not perfection. The goal is a longer average gap between events, a faster recovery when events happen, and a clearer understanding of the pattern over time.

---

## Contributing

Pull requests welcome. Priorities for contribution:

- Additional language translations
- More replacement behavior options
- Integration with calendar/reminders for scheduled check-ins
- Improved trigger pattern card formatting
- Post-session reflection templates

Please keep all additions consistent with the design principles: low shame, action-first, no preaching.

---

## License

MIT License. See `LICENSE` for details.
