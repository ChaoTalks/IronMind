# IronMind

<p align="center">
  <img src="assets/ironmind.png" alt="IronMind" width="180" />
</p>

<p align="center">
  <a href="README.zh-CN.md">中文</a>
</p>

Behavioral intervention skill for reducing or stopping compulsive pornography consumption and masturbation.

**If you work from home alone, this is the skill you need most.** No office. No colleagues. No external accountability. Just you, your screen, and no one checking. IronMind is built for exactly that situation.

**Action-first. Low-shame. No moralizing.**

Works with: Claude Code · Cursor · VS Code / GitHub Copilot · CodeBuddy · Codex CLI

---

## Design Principles

**1. Action before analysis.**
In an active urge, long reflection is the wrong tool. The skill gives one physical command first. Analysis comes later.

**2. Low shame, always.**
Relapse is treated as behavioral data, not moral failure. Shame accelerates relapse — it is never used as a motivator.

**3. No preaching.**
The skill does not explain why the behavior is harmful or push any value system. The user has already decided they want to change.

**4. Replacement, not suppression.**
Pure suppression fails under sustained pressure. The skill offers concrete replacement behaviors to redirect the behavioral chain before it completes.

**5. Short, direct responses.**
Response length is calibrated to state. Active urge gets a single imperative sentence. Calm check-in may get more.

**6. The user sets the goal.**
Supports reduction or full cessation. Does not impose a standard.

---

## User States

| State | When | Primary Goal |
|---|---|---|
| `stable` | Calm check-in, streak report | Pattern awareness, consistency |
| `warning` | Restless, near a trigger, drifting | Interrupt before momentum builds |
| `active_urge` | Active craving, urgency | Physical interruption first |
| `post_relapse` | After a relapse | Stop spiral, prevent second relapse |

When state is ambiguous between `warning` and `active_urge`, the skill defaults to `active_urge` protocol.

---

## Installation

### Claude Code

```bash
git clone https://github.com/your-org/IronMind ~/.claude/skills/urge-interrupt
```

Invoke with `/urge-interrupt` or `/ui`.

### Cursor

Copy `cursor/rules/urge-interrupt.mdc` to your project's `.cursor/rules/` directory.

### VS Code / GitHub Copilot

Copy `vscode/instructions/urge-interrupt.instructions.md` to your project's `.github/instructions/` directory.

### CodeBuddy

Copy `codebuddy/urge-interrupt/SKILL.md` into your CodeBuddy skills directory.

### Codex CLI

Copy `codex/urge-interrupt/SKILL.md` into your Codex skills directory.

---

## Usage

```
/urge-interrupt              # open check-in, state inferred from message
/urge-interrupt active       # jump to active_urge protocol
/urge-interrupt relapse      # jump to post_relapse protocol
/urge-interrupt review       # trigger map or weekly review
/urge-interrupt morning      # morning reminder
/urge-interrupt evening      # evening pre-window check
```

---

## Configuration

Copy `config.example.yaml` to `config.yaml` and adjust.

Key options:

```yaml
goal_type: cessation           # reduction | cessation
language: en                   # en | zh | es | fr | de
reminder_schedule: both        # morning | evening | both | off
reminder_tone: direct          # supportive | direct | clinical
intervention_intensity: medium # low | medium | high
active_urge_max_words: 40
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
| `supportive` | Warmer, slightly more encouraging |
| `direct` | Short, no-frills, action-focused (default) |
| `clinical` | Neutral, behavioral, minimal emotional framing |

### Intervention Intensity

| Level | Behavior |
|---|---|
| `low` | One suggestion, soft nudge |
| `medium` | Firm command + follow-up (default) |
| `high` | Repeated commands, escalating if no response |

---

## Example Dialogues

### Active Urge

```
User:  I need help right now I keep thinking about it
Agent: Stand up. Right now — go to a different room.

User:  okay I'm in the kitchen
Agent: Good. Fill a glass of water and drink it. Don't go back yet.

User:  done
Agent: You held. How long ago did it start?
```

### Post-Relapse

```
User:  I gave in. I'm such a mess.
Agent: It happened. That doesn't make you a mess. Close whatever led to it.
       Then come back.

User:  okay. I hate myself right now
Agent: That feeling is normal. It's also what pushes people toward doing
       it again. Eat something, drink water, don't be alone with your
       phone. What does the next hour look like?
```

### Warning State

```
User:  I'm kind of bored and lying in bed with my phone. It's late.
Agent: You caught it early. High-risk setup: bored, alone, late, phone
       in hand. Pick one: phone across the room and read something, or
       get up for 10 minutes.
```

### Stable Check-in

```
User:  Day 14. Just checking in.
Agent: Solid. Two weeks. What was the toughest moment and what got you through it?
```

### Trigger Mapping

```
User:  I want to understand why I keep slipping at night.
Agent: Let's map it. What time does it usually happen?

User:  11pm to 1am
Agent: Where are you — bedroom, phone, lights off?

User:  Yeah, in bed with my phone
Agent: What's the emotional state going in — bored, stressed, anxious?

User:  Usually bored and a little anxious about tomorrow
Agent: What's the first small step? Opening a specific app, searching something?

User:  Usually Instagram, then it goes from there
Agent:
       Trigger Pattern Snapshot
       ------------------------
       High-risk time:     11pm–1am
       High-risk location: Bedroom, dark, phone in hand
       Emotional state:    Bored + low-level anxiety
       First move:         Opening Instagram
       Suggested interrupt: Phone in another room before 10pm
```

---

## Repository Structure

```
IronMind/
├── skills/
│   └── urge-interrupt/
│       ├── SKILL.md                        # Canonical skill definition
│       └── references/
│           ├── trigger-map.md              # 3-tier trigger analysis framework
│           ├── reminder-templates.md       # Morning / evening / weekly templates
│           └── replacement-behaviors.md    # Full replacement behavior menu
├── cursor/
│   └── rules/
│       └── urge-interrupt.mdc              # Cursor IDE rule
├── vscode/
│   └── instructions/
│       └── urge-interrupt.instructions.md  # VS Code / GitHub Copilot
├── codebuddy/
│   └── urge-interrupt/
│       └── SKILL.md                        # CodeBuddy adaptation
├── codex/
│   └── urge-interrupt/
│       └── SKILL.md                        # Codex CLI adaptation
├── plugin.json                             # Plugin manifest
├── config.example.yaml                     # Configuration template
└── README.md
```

---

## What This Skill Does Not Do

- It is not therapy or clinical treatment.
- It does not store or transmit data outside your local environment.
- It does not connect to any external service.
- It does not moralize or push a value system.
- It does not replace professional support for addiction or mental health conditions.

If compulsive behavior significantly impairs daily functioning, please consider reaching out to a licensed therapist or counselor.

---

## Philosophy

Two failure modes define most habit-change tools:

**Shame spirals.** Treating relapse as moral catastrophe pushes users into "fuck it" binge behavior. Relapse → guilt → more relapse is worse than the original slip. The skill interrupts this chain explicitly.

**Passive motivation.** Reminding someone why a behavior is bad does nothing at peak urge. Motivation is the weakest lever when activation is highest. Physical interruption is the strongest one.

IronMind is built around both: zero drama after relapse, and physical-first when the window is open.

The goal is not perfection. It is a longer average gap between events, faster recovery when events happen, and a clearer pattern map over time.

---

## Contributing

Contributions welcome. Priorities:

- Additional language translations
- More replacement behavior options
- Improved trigger pattern card formatting
- Post-session reflection templates
- Integration with calendar/reminder APIs

Keep all additions consistent with the design principles: low shame, action-first, no preaching.

---

## License

MIT
