# 26. Hooks appendix

## Simple Explanation (like you're 5)

Hooks are the concrete places where you can insert your own control code into the agent’s life.

This appendix is the practical reference: the five important moments, the simple exit-code language, and three drills so the ideas stick.

## Key Concepts Unpacked

### The 5 moments that matter
- **SessionStart** — when a new session begins.
- **PreToolUse** — right before a tool is allowed to run (the most important gate).
- **PostToolUse** — right after a tool has run (for feedback and logging).
- **Stop** — when the agent wants to finish.
- **SubagentStop** — when a helper agent finishes.

### The exit-code contract
A simple, reliable way for a hook to say “success,” “failure,” or “block this action” back to the system (for example, exit code 2 as a hard stop).

### 3 drills
Hands-on exercises that force you to write and observe hooks in realistic situations.

### The exit-code contract, precisely
A hook is just a command that receives the event's details as JSON and answers with an exit code — but the meaning of that code depends on *which* moment it's attached to. Zero always passes. On the two **gate** events, `PreToolUse` and `Stop`, exit code `2` is special: it actually blocks the action or refuses to let the session finish, while any other non-zero code is a non-blocking error that stops nothing. On `PostToolUse`, the action has already run, so exit `2` cannot undo it — instead, whatever the hook printed to stderr gets fed back to the agent as its very next input. That's the real design surface: a hook that prints "blocked: tests failing in test/auth — fix those first" is simultaneously a guardrail and a self-healing error message, doing both jobs from Parts 2 and 3 at once.

### The three drills, made concrete
Drill 1 (**see the stream**) attaches a hook that appends one line per tool call to `trace.log`, then has you read it after one normal beat — most people are surprised how many actions a single beat actually takes, which is the whole point of observability. Drill 2 (**block on purpose**) writes a `PreToolUse` check that blocks any Bash command containing `curl`, with an error naming the allowed alternative, so you can watch the full cycle: blocked, informed, redirected. Drill 3 (**the conditional gate**) makes the test-suite `Stop` hook run only when source files actually changed in the beat (checked via `git diff --name-only`), which is how real harnesses stay fast enough that people keep using them instead of disabling the slow check.

## Why would this be on the exam?
Hooks are the main extension point for harness control in the tools the course uses. Familiarity with the five moments and the exit-code contract is expected.
