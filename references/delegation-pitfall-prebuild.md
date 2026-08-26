# Pre-build Pitfall

## The Pattern

You delegate a task to a specialist agent. Before invoking it, you scaffold code, configure files, write schema, or build part of the feature yourself.

## Why It Wastes Effort

1. **Merge friction:** The specialist starts from a different foundation. Your scaffolding conflicts with their structure.
2. **Wrote code that gets replaced:** The specialist ignores your structure and builds theirs. Your work is wasted.
3. **Defeats the purpose:** You delegated because the specialist should own the task. Pre-building means you did the work anyway.

## The Rule

> If you find yourself writing files before invoking the specialist, stop — the brief goes to the specialist, not the codebase.

## Real Session Example

**Task:** "Add tokenized public PDF links for driver dispatch"

**Wrong path (pre-build):**
1. You create the migration file
2. You add the column to schema.ts
3. You create the route handler stub
4. You delegate to Cursor: "Finish the PDF token feature"
5. Cursor ignores your stub, creates its own structure
6. Merge conflict. Your migration conflicts with Cursor's schema changes
7. You spend 30 minutes resolving conflicts

**Right path (delegate entirely):**
1. You write a CURSOR_BRIEF.md with the full contract
2. You delegate: "Implement the PDF token feature per this brief"
3. Cursor creates the migration, schema, route handler
4. Cursor validates with build + curl
5. Done in 10 minutes, zero conflicts

## The Trigger

You are about to write a file before invoking the specialist.

**STOP.** Write the brief instead. Let the specialist own the code.
