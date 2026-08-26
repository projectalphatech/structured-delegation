# Implementation Brief Example

## Task: Add tokenized public PDF links for driver dispatch

```markdown
PROJECT: Sharm Trips (travel booking platform)

WORKSPACE: /home/adham/projects/sharm-trips/

MODE: IMPLEMENTATION

OBJECTIVE: Add tokenized public PDF links for driver dispatch — the driver can open the dispatch manifest without logging in.

CONTEXT: Currently, dispatch PDFs are only accessible through the admin panel (requires login). Drivers need a public link they can tap on their phone. The link should be unguessable (UUID token), accessible without auth, and display inline in the browser.

REQUIREMENTS:
- Add `pdf_token` column to `dispatch_groups` table (UUID, unique)
- When generating dispatch PDF, create/reuse token
- Public route: `/api/d/<token>/` returns the PDF with `Content-Disposition: inline`
- WhatsApp message sent to driver includes the full public URL

CONSTRAINTS:
- No authentication on the public route (token is the access control)
- Token must be UUID v4 — unguessable
- PDF generation uses Cloudflare Browser Rendering API
- Must not break existing admin PDF download

SELECTED SKILLS:
- nextjs-cloudflare-deploy (for Cloudflare Workers patterns)
- systematic-debugging (if issues arise)

ALLOWED SCOPE:
- src/app/api/admin/dispatch/[groupId]/pdf/handlers.ts
- src/app/api/d/[token]/route.ts
- src/db/schema.ts
- migrations/

PROTECTED SCOPE:
- src/lib/auth.ts (don't touch auth system)
- src/app/admin/(console)/ (don't break existing admin routes)

ACCEPTANCE CRITERIA:
- `pdf_token` column exists in D1
- GET /api/d/<token> returns HTTP 200 with `application/pdf`
- GET /api/d/<token> works without any session/cookie
- GET /api/d/<invalid-token> returns HTTP 404

VALIDATION:
- `npx next build` passes
- `curl -sI https://<worker>/api/d/<valid-token>` returns 200
- `curl -sI https://<worker>/api/d/invalid-uuid` returns 404

STOP AND RETURN IF:
- Database migration conflicts with existing schema
- Cloudflare Browser Rendering format issue
- Unable to deploy for verification

RETURN:
- Summary of changes
- Files changed
- Migration SQL
- Live URL for testing
- Remaining risks
```
