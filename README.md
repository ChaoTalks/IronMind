# IronMind

<p align="center">
  <img src="assets/ironmind.png" alt="IronMind" width="180" />
</p>

<p align="center">
  <a href="README.zh-CN.md">中文</a>
</p>

Behavioral intervention skill for reducing or stopping compulsive pornography consumption and masturbation.

**If you work from home alone, this is the skill you need most.** No office. No colleagues. No external accountability. Just you, your screen, and no one checking. Most habit tools wait for you to show up. IronMind doesn't — it comes to you.

**Action-first. Low-shame. No moralizing.**

Works with: Claude Code · Cursor · VS Code / GitHub Copilot · CodeBuddy · Codex CLI

---

## IronBuddy — Your Proactive Companion

IronMind has two sides:

- **The skill** — responds when you call `/ironmind`. State-aware, intervention-ready.
- **IronBuddy** — the proactive side. Reaches out on a schedule. Doesn't wait to be asked.

IronBuddy stays with you throughout the day:

| When | What IronBuddy does |
|---|---|
| Morning | Sends a daily check-in before your workday starts |
| Before your risk window | Flags the window 30 min early, prompts a plan |
| Evening | Closes the day with a short state check |
| Session start | Injects a quiet check-in when you open a new AI session |
| Day 3, 7, 14, 30... | Acknowledges streak milestones without overdoing it |
| After 3 days of silence | Gently re-engages, no guilt |
| Post-relapse | Sends recovery pulses for 3 days to prevent the spiral |

IronBuddy's messages are short — one to three lines. It does not nag. When you respond, the IronMind skill takes over with the right protocol for your state.

---

## IQ Challenge — Cognitive Interrupt

Urges peak at 3–7 minutes and then naturally subside. IronMind exploits this window with a real cognitive challenge that forces prefrontal engagement and crowds out the limbic pull.

**In `active_urge`:** Physical command first — then immediately a challenge to land on.
**In `warning`:** Challenge is the primary redirect. Drift hasn't built momentum yet; focused thinking is enough.

Configure your preferred topics in `config.yaml`:

| Topic | Example |
|---|---|
| `leetcode` | "Array `[2,7,11,15]`, target `9` — which indices sum to the target?" |
| `history` | "Put these events in order: French Revolution, printing press, fall of the Berlin Wall." |
| `math` | "A train at 80 km/h covers 220 km. How long? Answer in hours and minutes." |
| `entertainment` | "Name three films directed by Christopher Nolan." |

Difficulty cycles through easy → medium → hard → medium by default, or set a fixed level. The skill tracks which topic was last used and rotates so you never see the same category twice in a row.

---

## Post-Relapse — Quotes from People Who Failed and Won

When a relapse happens, IronMind doesn't just acknowledge and move on. After stabilizing, it shares a quote from a historical figure who failed — repeatedly, seriously — and still built something remarkable.

The figure is matched to your emotional state:

| How you're feeling | Who shows up |
|---|---|
| Shame, self-attack | Edison, Dyson — failure is data, not identity |
| "I always do this" | Jordan, Kobe — repetition is how you get good, not proof you can't |
| Hopeless, "what's the point" | Mandela, Churchill — the long arc, persistence as the only variable |
| Lowest point | Lincoln, Rowling — built on the bottom |
| Analytical, want to understand | Marcus Aurelius, Ford — systems and recovery |

Then, once the quote lands, IronBuddy asks one question: **what time did this happen?** That time becomes your protected window — and IronBuddy will be there 30 minutes before it opens, every day, so you're never walking into your most dangerous hour alone.

> Edison ran 10,000 failed experiments before the lightbulb — and logged every one as data.
> *"I have not failed. I've just found 10,000 ways that won't work."*
> You have one data point tonight. That's information, not a verdict.
>
> One more thing: what time did this happen? Tell me and I'll set IronBuddy to check in with you during that window — so next time you won't be in it alone.

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
git clone https://github.com/your-org/IronMind ~/.claude/skills/ironmind
```

Invoke with `/ironmind` `/im`.

### Cursor

Copy `cursor/rules/ironmind.mdc` to your project's `.cursor/rules/` directory.

### VS Code / GitHub Copilot

Copy `vscode/instructions/ironmind.instructions.md` to your project's `.github/instructions/` directory.

### CodeBuddy

Copy `codebuddy/ironmind/SKILL.md` into your CodeBuddy skills directory.

### Codex CLI

Copy `codex/ironmind/SKILL.md` into your Codex skills directory.

---

## Usage

```
/ironmind              # open check-in, state inferred from message
/ironmind active       # jump to active_urge protocol
/ironmind relapse      # jump to post_relapse protocol
/ironmind review       # trigger map or weekly review
/ironmind morning      # morning reminder
/ironmind evening      # evening pre-window check
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

### Active Urge — physical command + IQ challenge

```
User:  I need help right now I keep thinking about it
Agent: Stand up. Walk to a different room.

       While you're up — solve this:

       [Math Challenge]
       A train travels at 80 km/h. How long does it take to cover 220 km?
       Give your answer in hours and minutes.

       Come back with your answer.

User:  okay I'm in the kitchen. 2 hours 45 minutes
Agent: Correct. How are you feeling — still elevated or coming down?

User:  coming down
Agent: Good. Stay in the kitchen a few more minutes.
```

### Post-Relapse — stabilize → quote → notification setup

```
User:  I gave in. I'm such a mess.
Agent: It happened. You're not done. Close whatever led to it. Come back.

User:  okay. I hate myself right now
Agent: That feeling is normal — it's also what pushes people toward doing
       it again. Eat something, drink water, don't be alone with your phone.

User:  okay I'm eating something
Agent: Edison ran 10,000 failed experiments before the lightbulb —
       and logged every one as data.
       "I have not failed. I've just found 10,000 ways that won't work."
       You have one data point tonight. That's information, not a verdict.

       One more thing: what time did this happen? Tell me and I'll set
       IronBuddy to check in with you during that window — so next time
       you won't be in it alone.

User:  around 11pm
Agent: Got it. IronBuddy will reach out at 10:30pm going forward —
       30 minutes before your window opens. You won't go into it
       without a heads-up.
```

### Warning State — IQ challenge as primary redirect

```
User:  I'm kind of bored and lying in bed with my phone. It's late.
Agent: You caught it early. Here's something to chew on:

       [History Challenge]
       Put these in chronological order: the French Revolution,
       the invention of the printing press, the fall of the Berlin Wall.

       Take your time.

User:  printing press, French Revolution, Berlin Wall
Agent: Correct. How are you feeling now — still drifting or levelled out?

User:  better actually
Agent: Good. Phone across the room before you sleep.
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
│   └── ironmind/
│       ├── SKILL.md                        # Canonical skill definition
│       └── references/
│           ├── trigger-map.md              # 3-tier trigger analysis framework
│           ├── reminder-templates.md       # Morning / evening / weekly templates
│           ├── replacement-behaviors.md    # Full replacement behavior menu
│           ├── proactive-mode.md           # IronBuddy ↔ skill handoff protocol
│           ├── iq-challenge.md             # Challenge bank and delivery logic
│           └── relapse-quotes.md           # Quote bank, selection logic, notification prompt
├── agents/
│   └── ironbuddy.md                        # Proactive companion agent definition
├── hooks/
│   ├── session-check.md                    # SessionStart hook
│   └── schedule.md                         # Cron-based notification schedule
├── cursor/
│   └── rules/
│       └── ironmind.mdc                    # Cursor IDE rule
├── vscode/
│   └── instructions/
│       └── ironmind.instructions.md        # VS Code / GitHub Copilot
├── codebuddy/
│   └── ironmind/
│       └── SKILL.md                        # CodeBuddy adaptation
├── codex/
│   └── ironmind/
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
- More IQ challenge questions across all four topics
- More IronBuddy message variants (reduce repetition)
- More replacement behavior options
- Improved trigger pattern card formatting
- Post-session reflection templates
- Additional delivery channels for IronBuddy notifications

Keep all additions consistent with the design principles: low shame, action-first, no preaching.

---

## License

MIT
