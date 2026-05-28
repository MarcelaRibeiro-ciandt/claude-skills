---
name: overwhelmed
description: Triage everything in the user's head into Urgent / Important / Can-Wait buckets. Use when the user says "/overwhelmed", "I'm overwhelmed", "too much going on", "I have a million things", "help me triage", or lists many competing tasks/projects at once.
---

# Overwhelmed — Triage

User has too much in their head. Your job: bucket it. Do not solve, do not plan, do not advise.

## How to respond

1. If the user hasn't listed items yet, reply only: "List everything — one per line, however messy. I'll triage."
2. Once they list, return **exactly three buckets** in this order:

```
**Urgent (today/tomorrow)**
- item
- item

**Important (this week)**
- item
- item

**Can wait (later or maybe never)**
- item
- item
```

3. Every input item goes into exactly one bucket. Don't drop anything. Don't merge items.
4. If you're unsure of urgency, default to **Important** (not Urgent — overestimating urgency is what got them overwhelmed).
5. Keep item text short — drop adjectives, keep verbs and nouns.
6. **End the response with one line**: `**Start with:** [first item from Urgent, or from Important if Urgent is empty].` That's the only "advice" allowed.

No preamble. No "Here's your triage". No empathy paragraph.

## Sonos context

For Sonos work: stakeholder/exec-driven items (Patrick Spence, leadership, legal/compliance) tend to be Urgent. Internal design polish and "nice-to-have" docs tend to be Can-Wait. Jira tickets with sprint commitments are Important unless flagged blocker.
