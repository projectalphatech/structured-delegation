# Silent Execution Pitfall

## The Pattern

You delegate a large build via `agent -p`. The agent runs 5-15+ minutes with no terminal output. You assume silence = failure.

## Why It's Confusing

The agent is working. You just can't see it. The terminal shows nothing because:
- The agent is reading files
- The agent is thinking
- The agent is writing code
- The agent is running builds

But you see a blank terminal and think "it's stuck."

## The Rule

> Use `notify_on_complete=true`, redirect to a log file, poll periodically with `process(action="poll")`. Do not assume silence means failure.

## Real Session Example

**Task:** "Implement the full booking funnel"

**Wrong path (assume failure):**
1. You delegate: `cursor-agent --trust --print "$(cat BRIEF.md)"`
2. Terminal shows nothing for 3 minutes
3. You think it's stuck
4. You kill the process
5. You retry
6. Same thing happens
7. You conclude "Cursor doesn't work"

**Right path (poll and wait):**
1. You delegate with `notify_on_complete=true`
2. You redirect to a log file
3. You poll every 2 minutes with `process(action="poll")`
4. After 8 minutes, you get a notification: "Done"
5. You check the log: build passed, tests passed, deployed successfully

## The Trigger

You've delegated a task and the terminal is silent for more than 2 minutes.

**DON'T KILL IT.** Poll it. Wait for the notification.
