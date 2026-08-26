# Planning Brief Example

## Task: Plan a custom CRM system

```markdown
PROJECT: New Client CRM

MODE: PLANNING

OBJECTIVE: Produce a technical plan for a custom CRM system for a client who manages 500+ customers, needs lead tracking, sales pipeline, and WhatsApp integration.

CONTEXT: The client currently uses Excel. They have a sales team of 5 people. Need mobile-friendly access. Must support Arabic and English. Integration with their existing WhatsApp Business number.

REQUIREMENTS (high-level):
- Lead management (create, update, assign, track)
- Sales pipeline (stages: new → contacted → qualified → proposal → won/lost)
- WhatsApp integration (send message to lead from the CRM)
- Mobile-friendly (team uses phones primarily)
- Bilingual: Arabic (primary) and English
- User roles: admin and sales rep

CONSTRAINTS:
- Must run on Cloudflare Workers (existing infrastructure)
- D1 database (SQLite at edge)
- No monthly SaaS fees — client owns everything
- Auth: simple credentials (no OAuth complexity)

EXPECTED OUTPUT:
- Recommended architecture (pages, routes, components)
- Data model (tables, relationships)
- Component structure
- Key workflows (how a lead moves through the system)
- Integration approach (WhatsApp — wa.me links or API?)
- Implementation milestones (6 phases)
- Major risks and unknowns
```
