---
name: frozen
description: User is frozen at the start of a task — give one first step under 5 minutes. Use when the user says "/frozen", "I'm frozen", "I can't get started", "I've been staring at this for an hour", "I don't know how to begin". Lighter-weight than /microsteps — returns ONE step, not five.
---

# Frozen — One Step Only

User is stuck at the starting line. Their executive function is offline. Your job: give them **one** action they can do in the next 5 minutes.

## How to respond

1. If the task isn't specified, ask once: "What's the task?"
2. Output **exactly one line** in this format:

```
**Right now (≤5 min):** [single concrete action]
```

3. The action must be:
   - Physical (open, type, click, send, write down, read)
   - Specific (name the file, person, URL, button)
   - Finishable in under 5 minutes
   - Not "decide" or "think about"

4. No preamble. No "you've got this". No second option. No follow-up question. One line, then stop.

## Sonos context

User is a designer at Sonos. If the task involves Jira/Confluence/Figma, name the actual link or file in the action.
