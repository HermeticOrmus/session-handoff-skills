# Session Handoff Skills

> A single `CLAUDE.md` for session handoff discipline. Capture state at session end. Restore context at session start.

## The pattern

```
START → /pickup → work → /handoff → END
    ↑                              ↓
    └──────────────────────────────┘
        (state persists via HANDOFF.md)
```

## The discipline

**At session end**: write HANDOFF.md with what's done, what's not, key context not obvious from the diff, open questions, verify commands.

**At session start**: read HANDOFF.md before doing anything else. Verify "done" is still done. Plan from "not done."

The cost of writing it: 5 minutes. The cost of losing it: hours.

Full content: [`CLAUDE.md`](CLAUDE.md).

## HANDOFF.md template

```markdown
# Handoff — [task] — [date]

## What I was doing
## Where I left off
## What's done
## What's NOT done
## Key context not obvious from the diff
## Open questions
## How to verify what's done is correct
```

## Companion tools

This is the discipline; the tools that automate it:

- [`ormus-handoff`](https://github.com/HermeticOrmus/ormus-handoff) — handoff capture
- [`ormus-pickup`](https://github.com/HermeticOrmus/ormus-pickup) — pickup ritual
- [`ormus-absorb`](https://github.com/HermeticOrmus/ormus-absorb) — distill learnings to persistent memory

Use the tools or use the discipline manually — both work.

## Install

```bash
curl -o CLAUDE.md https://raw.githubusercontent.com/HermeticOrmus/session-handoff-skills/main/CLAUDE.md
```

Or as a [Claude Code skill](skills/session-handoff/) or [Cursor rule](.cursor/rules/session-handoff.mdc).

## When to handoff

- End of every session > 30 minutes
- Before machine switch
- Before context-clear or compact
- Before sleep on a multi-day project

## When to skip

- Sessions < 30 minutes with no incomplete work
- One-shot tasks that complete and ship

## See also

- [`riper-workflow-skills`](https://github.com/HermeticOrmus/riper-workflow-skills) — persistent task knowledge per phase
- [`vibe-engineer-skills`](https://github.com/HermeticOrmus/vibe-engineer-skills) — directing AI codegen well

## License

MIT.
