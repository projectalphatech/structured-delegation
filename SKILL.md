---
name: structured-delegation
description: Delegate to AI agents without the build-loop pain. Prevents the three most common delegation failures — scaffolding before handing off, lightweight models stuck in fix loops, and silent execution. Use when delegating software implementation, research, or commercial analysis to any AI agent.
---

# Structured Delegation

## When to use this skill

Invoke this skill when the user asks to delegate a task to an AI agent, when you observe delegation anti-patterns (pre-build traps, build loops, silent execution), or when writing a structured brief for specialist agent handoff.

## What this skill provides

This skill documents the **structured brief pattern** — the industry-standard approach for reliable delegation to AI agents. It prevents the three most common failures:

1. **Pre-build trap** — scaffolding code before delegating creates merge friction. The fix: delegate the ENTIRE build. Don't write files first.
2. **Build loop** — lightweight models writing code break the build repeatedly. The fix: lightweight models must NOT write code — write a brief and delegate immediately.
3. **Silent execution** — agents run with no output, user assumes failure. The fix: use `notify_on_complete=true`, redirect to log, poll periodically.

## How to apply

### 1. Write a structured brief

Every delegation needs: objective, requirements, constraints, acceptance criteria, validation steps, and stop conditions.

See `examples/` directory for templates:
- `IMPLEMENTATION_BRIEF.md` — software builds
- `RESEARCH_BRIEF.md` — discovery tasks
- `PLANNING_BRIEF.md` — architecture planning
- `COMMERCIAL_BRIEF.md` — business analysis
- `ESCALATION_BRIEF.md` — escalating to senior agents

### 2. Route to the right specialist

| Task Type | Specialist |
|---|---|
| Software implementation | Cursor, Claude Code, Codex |
| Research/Discovery | Scout, web search |
| Commercial intelligence | Meter, market research |
| Lightweight reasoning | Do directly |
| Difficult technical reasoning | Architect (escalation only) |

### 3. Validate with evidence

Never accept "it works" without proof. Build passes, tests pass, lint clean for code. Browser verification for frontend.

## References

- [Pre-build pitfall](references/delegation-pitfall-prebuild.md)
- [Build loop pitfall](references/delegation-pitfall-longcat-build-loop.md)
- [Silent execution pitfall](references/delegation-pitfall-silent.md)

