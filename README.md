<div align="center">

# 📋 structured-delegation

**Delegate to AI agents without the pain.**

*The structured brief pattern that prevents the 3 most common delegation failures: pre-build traps, build loops, and silent execution.*

## 📸 Demo

![Structured Delegation Flow](https://github.com/projectalphatech/structured-delegation/blob/main/assets/delegation-flow.png)

<!-- Placeholder image — replace with a real diagram of the delegation flow -->

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Agent OS](https://img.shields.io/badge/Part_of-agent--os-6B46C1)](https://github.com/projectalphatech/agent-os)
[![Stars](https://img.shields.io/github/stars/projectalphatech/structured-delegation?style=social)](https://github.com/projectalphatech/structured-delegation)

[Quick Start](#-quick-start) •
[The 3 Traps](#-the-3-traps) •
[Pattern](#-the-pattern) •
[References](references/) •
[Examples](examples/)

</div>

---

## 🤔 Why this exists

You delegated a task to an AI agent. It failed. You don't know why.

**The 3 most common delegation failures:**

| Trap | What happens | The fix |
|---|---|---|
| **Pre-build trap** | You scaffold code before delegating → merge friction | Delegate the ENTIRE build. Don't write files first. |
| **Build loop** | Lightweight model writes code → breaks → patches → breaks again | Lightweight models must NOT write code. Write a brief and delegate. |
| **Silent execution** | Agent runs 15 min with no output → you think it failed | Use notify_on_complete, redirect to log, poll periodically. |

This skill documents the pattern that prevents all three.

---

## ✨ What you get

| Feature | Status |
|---|---|
| **Structured brief template** | Objective, constraints, acceptance criteria, stop conditions |
| **Routing matrix** | Which specialist for which task |
| **Anti-pattern documentation** | 3 session-derived pitfalls with fixes |
| **Planning gate** | Require plan before implementation |
| **Evidence-based validation** | Never accept "it works" without proof |

---

## 🚀 Quick Start

### 1. Write a structured brief

```markdown
PROJECT: Travel Booking System
WORKSPACE: /home/adham/projects/sharm-trips/

OBJECTIVE: Add tokenized public PDF links for driver dispatch

REQUIREMENTS:
- Add pdf_token column (UUID, unique)
- Public route: /api/d/<token>/ returns PDF inline
- WhatsApp message includes public URL

CONSTRAINTS:
- No auth on public route (token is access control)
- Must not break existing admin PDF download

ACCEPTANCE CRITERIA:
- GET /api/d/<token> returns 200 with application/pdf
- GET /api/d/<invalid-token> returns 404

VALIDATION:
- npx next build passes
- curl -sI https://<worker>/api/d/<token> returns 200

STOP AND RETURN IF:
- Database migration conflicts with schema
- Cloudflare Browser Rendering format issue
- Unable to deploy for verification
```

### 2. Route to the right specialist

| Task Type | Specialist |
|---|---|
| Software implementation | Cursor, Claude Code, Codex |
| Research/Discovery | Scout, web search |
| Commercial intelligence | Meter, market research |
| Lightweight reasoning | Do directly |
| Difficult technical reasoning | Architect (escalation only) |

### 3. Validate with evidence

| Work Type | Evidence Required |
|---|---|
| Code changes | Build passes, tests pass, lint clean |
| Frontend work | Browser verification, responsive checks |
| Research | Sources cited, findings structured |
| Commercial analysis | Data referenced, unknowns flagged |

---

## 💀 The 3 Traps

### Trap 1: Pre-build

**The pattern:** You scaffold, configure, write schema, or build anything before invoking the specialist.

**Why it wastes effort:** The specialist starts from a different foundation. Your scaffolding creates merge friction. The specialist ignores your structure and builds theirs.

**The rule:** If you find yourself writing files before invoking the specialist, stop — the brief goes to the specialist, not the codebase.

→ [Full reference](references/delegation-pitfall-prebuild.md)

### Trap 2: Build loop

**The pattern:** A lightweight reasoning model writes code → breaks the build → patches it → breaks it again.

**Why it costs turns:** Each fix-loop costs 2-3 turns. After 3 attempts, you've spent 6-9 turns with nothing working.

**The rule:** Lightweight models must NOT write code. Write a CURSOR_BRIEF.md and delegate immediately. Trigger: you are writing a build file, or a build has failed twice in a row.

→ [Full reference](references/delegation-pitfall-longcat-build-loop.md)

### Trap 3: Silent execution

**The pattern:** You delegate a large build via `agent -p`. The agent runs 5-15+ minutes with no terminal output. You assume silence = failure.

**Why it's confusing:** The agent is working. You just can't see it.

**The rule:** Use `notify_on_complete=true`, redirect to a log file, poll periodically with `process(action="poll")`. Do not assume silence means failure.

→ [Full reference](references/delegation-pitfall-silent.md)

---

## 🏗️ The pattern

```
UNDERSTAND OBJECTIVE
↓
COMPILE STRUCTURED BRIEF
↓
ROUTE TO SPECIALIST
↓
PLANNING GATE (specialist plans before building)
↓
EXECUTE
↓
VALIDATE WITH EVIDENCE
↓
REPORT
```

---

## 📚 References

- [Pre-build pitfall](references/delegation-pitfall-prebuild.md)
- [Build loop pitfall](references/delegation-pitfall-longcat-build-loop.md)
- [Silent execution pitfall](references/delegation-pitfall-silent.md)
- [Cursor CLI reference](references/cursor-cli.md)
- [Envelope encryption technique](references/technique-envelope-encryption.md)
- [GSC OAuth technique](references/technique-gsc-oauth.md)

---

## 📖 Examples

- [Research brief](examples/RESEARCH_BRIEF.md)
- [Implementation brief](examples/IMPLEMENTATION_BRIEF.md)
- [Planning brief](examples/PLANNING_BRIEF.md)
- [Commercial brief](examples/COMMERCIAL_BRIEF.md)
- [Escalation brief](examples/ESCALATION_BRIEF.md)

---

## 🔗 Part of the Project Alpha ecosystem

- [agent-os](https://github.com/projectalphatech/agent-os) — the operating system for coordinating specialized AI agents
- [structured-delegation](https://github.com/projectalphatech/structured-delegation) — delegation briefs + anti-patterns that prevent build failures
- [arabic-edge-pdf](https://github.com/projectalphatech/arabic-edge-pdf) — Arabic PDF generation at the edge, zero tofu, zero libraries
- [gps-cluster-engine](https://github.com/projectalphatech/gps-cluster-engine) — group GPS points by proximity with capacity constraints
- [nextjs-cloudflare-deploy](https://github.com/projectalphatech/nextjs-cloudflare-deploy) — the definitive Next.js + Cloudflare Workers deployment guide

---

## 📄 License

MIT © [Project Alpha Tech](https://projectalpha.tech)

---

<div align="center">

**⭐ Star this repo if you've ever been stuck in a build loop!**

</div>
