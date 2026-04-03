# Replacement Behavior Menu — Reference

Offer as options, not commands. Let the user choose. Match the option to their current state and environment.

## Physical (Fast — under 2 minutes)
- 20 pushups or jumping jacks
- Cold water on face or wrists
- 10 slow deep breaths
- Stand up and walk to another room

## Physical (Medium — 5–15 minutes)
- Walk outside (even just around the block)
- Shower (cold if possible)
- Any exercise: run, lift, stretch

## Environmental
- Put device in another room
- Turn the lights on
- Move to a different room
- Go somewhere with other people (café, common area)

## Cognitive Redirect
- Write one sentence about what triggered this
- Name the emotion underneath the urge (bored / lonely / anxious / tired)
- Open a task or project you've been avoiding
- Set a 5-minute timer and do one small productive thing

## Social
- Text someone (no need to explain why — just make contact)
- Call a friend or family member
- Check into a relevant online community

## Absorption (for sustained redirection)
- Watch something engaging: documentary, sport, comedy — not passive scrolling
- Play a game that requires active focus
- Read something physical (book preferred over phone)

---

## Selection Guidance

| State | Best Options |
|---|---|
| `active_urge` | Physical (fast), Environmental — immediate, no thought required |
| `warning` | Physical (fast or medium), Environmental, Cognitive |
| `stable` | Any — good time to plan which you'll use next time |
| `post_relapse` | Social, Absorption — avoid being alone with device |

## Configuring Defaults

Set preferred options in `config.yaml` under `default_interruption_actions`. The skill surfaces these first before offering the full menu.
