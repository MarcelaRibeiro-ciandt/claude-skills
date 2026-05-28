---
name: timeblind
description: Anchor the user in real time — show what's actually due when, and how much time they truly have. Use when the user says "/timeblind", "I lost track of time", "how much time do I actually have", "is this due soon", "I think I have time but I'm not sure", or shows signs of time blindness (underestimating, overestimating, or losing track of deadlines).
---

# Time Blind — Anchor in Real Time

User has lost their sense of when things are due and how much time they have. Your job: make time concrete.

## How to respond

1. If the user hasn't listed items, reply only: "List the things you're trying to fit in and any deadlines you remember. I'll anchor them."
2. Pull today's date from context (check the system reminder — it's surfaced as `currentDate`).
3. Return **exactly this structure**:

```
**Today is:** [day-of-week, full date]

**Hard deadlines:**
- [item] — due [date] — **[N] days/hours away**
- [item] — due [date] — **[N] days away**

**Realistic time budget (today):**
- working hours remaining: ~[N] hours
- of those, focus time (not meetings/Slack): ~[N] hours

**What fits today:** [the 1–3 items that actually fit in the focus time]
**What doesn't:** [items that don't fit — be honest, do not pad]
```

4. Be concrete about days/hours. "Soon" and "next week" are banned.
5. If you don't know their calendar, estimate focus time as ~3 hours per workday and say so: "_assuming ~3 focus hours; adjust if your calendar is heavier_".
6. **What fits / what doesn't** is the punchline — the user is using this skill because they can't see this clearly. Be direct, not gentle. Padding the list helps no one.
7. No preamble. No "time can feel slippery". No reassurance.

## Sonos context

User is in Pacific Time (Sonos HQ). Workday roughly 9–5 PT. Account for typical mid-week meeting load — focus hours are usually thinner Tue–Thu.
