# CLAUDE.md

Session handoff discipline. Capture state at session end. Restore context at session start.

**Tradeoff**: bias toward writing-it-down over remembering-later. The cost of a HANDOFF is 5 minutes; the cost of losing context is hours.

## The two-sided ritual

### At session end: handoff

Before closing the session, write a HANDOFF.md capturing:

```markdown
# Handoff — [task slug] — [ISO date]

## What I was doing
[1-2 sentences of context: what task, what stage]

## Where I left off
[Specific file:line if mid-edit; specific phase if mid-RIPER; specific test if mid-debug]

## What's done
- [Concrete completions, with file paths]

## What's NOT done
- [Specifically what remains, with the next step]

## Key context not obvious from the diff
- [Decisions, assumptions, reasoning that won't show in git log]
- [Things to NOT do (false leads explored)]
- [References to read first on resume]

## Open questions
- [Things I wasn't sure about, that need answering before continuing]

## How to verify what's done is correct
[Specific commands or checks to run on resume]
```

The HANDOFF lives at the project root or `~/dev/[task]/HANDOFF.md`. Git-tracked so it survives.

### At session start: pickup

Before doing anything else:

1. Read HANDOFF.md (if it exists). Do not skip.
2. Verify "what's done" is still done (commands from the verify section). State may have drifted while you were away.
3. Read the "Key context not obvious from the diff" section twice. This is the highest-leverage info.
4. Plan the next session's work based on "What's NOT done."
5. Update HANDOFF.md or supersede it with a new one as you work.

## When to handoff

- End of every session that ran > 30 minutes
- Before switching machines (Sun → Moon, etc.)
- Before context-clear or compact
- Before sleep on a multi-day project
- Before any interruption longer than 4 hours

Skip handoff for: sessions < 30 minutes with no incomplete work; one-shot tasks that complete and ship.

## What HANDOFF.md is NOT

- A diary of what you did (the git log handles that)
- A summary of the code (the diff handles that)
- A status report (it's for future-you, not for stakeholders)
- A replacement for committing your work (always commit before handoff)

## What HANDOFF.md IS

- The minimum context required to pick up exactly where you stopped
- The decisions and assumptions that won't show in git
- The verification commands that prove "done" is still done
- The map of what's NOT done with next steps explicit

## When the handoff is to someone else (not future-you)

Add:

- Recipient's name + their context
- Why this work matters to them
- What you'd appreciate them doing FIRST when they pick up

If handing off to a teammate, link to the relevant project memory file, the relevant docs, the running ticket. Don't make them archeologize.

## The session lifecycle

```
START → /pickup → work → /handoff → END
    ↑                              ↓
    └──────────────────────────────┘
         (state persists via HANDOFF.md)
```

The companion tools that automate this lifecycle:

- [`ormus-handoff`](https://github.com/HermeticOrmus/ormus-handoff) — handoff capture tool
- [`ormus-pickup`](https://github.com/HermeticOrmus/ormus-pickup) — pickup ritual tool
- [`ormus-absorb`](https://github.com/HermeticOrmus/ormus-absorb) — distill what was learned into persistent memory

This CLAUDE.md is the *discipline* behind the tools. You can use the discipline without the tools, but the tools encode the same patterns.

## Anti-patterns

- **Trusting memory** — "I'll remember tomorrow." You won't.
- **Handoff that restates the git log** — adds no value over `git log`.
- **Handoff without verify commands** — no way to know if "done" stayed done.
- **Pickup that skips reading the handoff** — guarantees re-discovering what was already learned.
- **One HANDOFF.md for everything** — should be task-scoped, not global. Multiple in-flight tasks = multiple HANDOFFs.
- **Handoff in conversation** — if it's not in a file, it's lost when the session clears.

---

**License**: MIT.
