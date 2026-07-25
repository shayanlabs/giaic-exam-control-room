# 13. Part 2 — The Heartbeat

## Simple Explanation (like you're 5)

The heartbeat is whatever wakes the loop up and starts a new run.

Without a heartbeat the loop never starts.
With a bad heartbeat it either never stops or keeps spending money for no good reason.

## Key Concepts Unpacked

### Four kinds of heartbeat
- **In-session**: runs while you are watching. Useful while you are still building and testing.
- **Conditional** (the `/goal` style): keeps going until a success condition is true.
- **Scheduled** (Routines): fires on a clock — every morning, every hour, etc.
- **Event-driven**: fires when something happens outside (a new pull request, a new ticket, a webhook).

### Three stop conditions
A good loop needs clear ways to stop:
1. **Success** — the goal is met.
2. **Limit** — max steps, max time, or max money reached.
3. **No-progress check** — it is going in circles and making no real progress.

### The Ralph loop
A named pattern for certain kinds of persistent, goal-seeking loops that keep working until the goal is truly done.

### The doom loop
The dangerous pattern where the loop keeps running, spending tokens, and either doing nothing useful or making things worse. The no-progress check is the main defense against it.

### Where the timer lives
A loop is never a single action — it's "do this, wait, do it again," so something has to stay awake between beats. An **in-session heartbeat** (like Claude Code's `/loop`) keeps its timer inside your open terminal session; close the session and the timer dies with it, because nothing of yours is left running. A **scheduled task or Routine** moves the timer *outside* the session onto a scheduler that never sleeps (cron on your own machine, or Anthropic's servers for a cloud Routine) — each tick launches a brand-new short-lived run, lets it finish, and shuts it down. That's the real difference between "watch this while I'm here" and "run this while I sleep."

### Choosing the right heartbeat: does it end, or does it repeat?
Before reaching for any heartbeat, ask one question about the task. If the task **ends** and a command can prove the end (like "tests pass"), use a conditional loop — it starts now and runs until done. If the task **repeats**, use a schedule or an event. If the task **happens once**, don't build a loop at all — an ordinary one-turn session is still the right tool for most work. A concrete example of the scheduled option: Claude Code Routines had launch-time daily caps of roughly 5 runs on Pro, 15 on Max, and 25 on Team/Enterprise, and by default they can only push to branches named `claude/*` — never straight to `main` — so unattended work stays safe from day one even before a human looks at it.

## Why would this be on the exam?
Without a reliable heartbeat and clear stop conditions a loop is either asleep or dangerous. The exam wants you to know the options and the failure modes.
