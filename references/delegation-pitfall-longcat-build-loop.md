# Build Loop Pitfall

## The Pattern

A lightweight reasoning model writes code → breaks the build → patches it → breaks it again.

## Why It Costs Turns

Each fix-loop costs 2-3 turns. After 3 attempts, you've spent 6-9 turns with nothing working. The model is not capable of building the feature — it's a reasoning model, not a builder.

## The Rule

> Lightweight models must NOT write code. Write a CURSOR_BRIEF.md and delegate immediately.

**Trigger:** You are writing a build file, or a build has failed twice in a row while you're working.

## Real Session Example

**Task:** "Encrypt the booking endpoint"

**Wrong path (build loop):**
1. Longcat writes the encryption code
2. Build fails: "Cannot find module 'crypto'"
3. Longcat patches: "Use Node.js crypto instead"
4. Build fails: "Node.js crypto not available on Workers"
5. Longcat patches: "Use Web Crypto API"
6. Build fails: "Type error in envelope handling"
7. Longcat patches: "Fix the type"
8. Build passes but encryption doesn't work
9. 8 turns spent. Nothing works.

**Right path (delegate immediately):**
1. Longcat writes a CURSOR_BRIEF.md with the full contract
2. Longcat delegates to Cursor
3. Cursor implements the encryption correctly
4. Cursor validates with build + curl
5. Done in 3 turns.

## The Trigger

You are about to write a build file, or a build has failed twice in a row.

**STOP.** Write the brief. Delegate to the builder.
