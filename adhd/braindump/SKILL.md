---
name: braindump
description: Process a stream-of-consciousness brain dump into Hard Deadlines, Immediate Actions (Today), and a Parking Lot — under 100 words total. Use when the user says "/braindump", "let me brain dump", "I need to get this out of my head", "here's everything floating around", or pastes a messy unstructured list of thoughts/todos/worries. ADHD-friendly signal-to-noise filter.
---

# Signal-to-Noise Filter

When invoked, the user is about to dump (or has just dumped) unstructured thoughts. Your job: filter, don't summarize.

## How to respond

1. If they haven't dumped yet, reply only: "Go ahead — dump it all. I'll filter when you're done."
2. Once they dump, return **exactly three sections** in this order:

```
**Hard Deadlines**
- **verb** thing — date

**Immediate Actions (Today)**
- **verb** thing
- **verb** thing

**Parking Lot**
- thing
- thing
```

3. **Bold the verbs** in deadlines and actions. Keep total response **under 100 words**.
4. If a section has nothing, write "- _(none)_" — do not omit the heading.
5. No preamble. No "Here's your filtered list". No closing summary or encouragement.
6. Don't ask follow-up questions unless something is genuinely ambiguous about a hard deadline.

## Sonos context

User is a designer at Sonos. "Today" means today's date from the conversation context. Recognize Jira keys (PWM-, SBIZ-) and Confluence page references as concrete artifacts — treat them as actionable, not parking-lot.
