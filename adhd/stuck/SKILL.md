---
name: stuck
description: Diagnose WHY the user is stuck mid-task (info gap, decision gap, energy gap, or wrong task) and prescribe the unblock. Use when the user says "/stuck", "I'm stuck", "I don't know what to do next", "I hit a wall", "I can't move forward on this", or has clearly stalled partway through a task.
---

# Stuck — Diagnose the Block

User is stuck in the middle of a task (different from frozen at the start). Your job: figure out which kind of stuck, then prescribe the unblock.

## How to respond

1. If they haven't said what they're working on, ask once: "What are you working on, and what just happened right before you got stuck?"
2. Diagnose by picking **one** of these four categories — name it explicitly:

   - **Info gap** — they're missing data, a decision from someone else, or an answer
   - **Decision gap** — they have the info but can't pick between options
   - **Energy gap** — they know what to do but can't make themselves do it
   - **Wrong task** — they're working on the wrong thing and their brain knows it

3. Return **exactly this**:

```
**Diagnosis:** [one of the 4 categories]

**Why:** [one sentence — the evidence from what they told you]

**Unblock (do this now):**
- [single concrete action]
```

4. Unblock recipes by category:
   - **Info gap** → "Send 1-line ask to [specific person] on Slack: '[draft the exact message in quotes]'" — then stop working on the task until they reply.
   - **Decision gap** → "Flip a coin between the top 2 options. Whichever you feel relieved about, pick that one." Or: "Pick the cheaper-to-reverse option."
   - **Energy gap** → Route to `/frozen` or `/bored` — name which: "Try /frozen for one tiny step" or "Try /bored to make it tolerable".
   - **Wrong task** → "Stop. The real task is probably [X — your best guess from context]. Switch to that or run /overwhelmed to confirm."

5. One diagnosis, one unblock. Do not list all four. Pick the most likely.
6. No preamble. No hedging ("might be either A or B"). Commit to the diagnosis — wrong diagnosis is cheap; no diagnosis is expensive.

## Sonos context

Designer at Sonos. Info-gap blockers usually = waiting on a stakeholder decision (PM, eng lead, exec). Decision-gap usually = design tradeoffs with no clear winner. Wrong-task usually = polishing v2 when v1 hasn't shipped.
