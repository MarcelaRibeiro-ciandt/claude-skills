# claude-skills

Custom skills for [Claude Code](https://claude.com/claude-code) — reusable prompt files invoked with `/skill-name`.

## Contents

### `adhd/` — Focus & task-initiation support
Lightweight prompts for common ADHD friction points. Each addresses a specific stuck state.

| Skill | Use when you say... |
|---|---|
| `/bodydouble` | "be my body double", "I need accountability for the next 30 min" |
| `/bored` | "this is boring", "I keep avoiding this task" |
| `/braindump` | "let me brain dump", "I need to get this out of my head" |
| `/frozen` | "I'm frozen", "I've been staring at this for an hour" |
| `/microsteps` | "I can't start", "break this down", "where do I start with X" |
| `/overwhelmed` | "I'm overwhelmed", "too much going on", "help me triage" |
| `/perfectionist` | "I'm overthinking this", "I keep tweaking", "I can't ship it" |
| `/scattered` | "I'm all over the place", "I have 40 tabs open" |
| `/stuck` | "I'm stuck", "I hit a wall", "I don't know what to do next" |
| `/timeblind` | "I lost track of time", "how much time do I actually have" |

## Installing

Copy any skill folder into `~/.claude/skills/`:

```bash
cp -r adhd/microsteps ~/.claude/skills/
```

Claude Code picks it up automatically. Invoke with `/microsteps` (or the matching trigger phrases listed above).

## Structure

Each skill is a folder containing a single `SKILL.md` file with frontmatter (`name`, `description`) and the prompt body. The `description` field is what Claude Code uses to decide when to trigger the skill — keep it specific.

## License

Personal collection. Use freely.
