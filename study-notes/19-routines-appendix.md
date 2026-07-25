# 19. Routines appendix

## Simple Explanation (like you're 5)

Routines are Claude Code’s built-in way to run work in the cloud without you watching.

This appendix is the practical field guide: every form field you fill in, every way a Routine can start, how secrets are handled, and the safety limits you must respect.

## Key Concepts Unpacked

### Every form field
The concrete boxes you fill when you create a Routine: the prompt, which repositories it can touch, which connectors it may use, the schedule, etc.

### All 3 triggers
The different ways a Routine can be started (time-based, event-based, and the third supported type).

### Secrets
How passwords and API keys are stored and given to the Routine safely so they do not appear in logs or in the prompt text.

### The two-routine gate
A practical safety rule that limits how Routines can start other Routines. It prevents runaway chains of automation.

### The claude-branch rule
A concrete rule about which Git branch a Routine is allowed to work on (usually a special branch). This stops the Routine from accidentally damaging the main line of work.

### Daily run caps
Hard limits on how many times a Routine can fire in one day. They protect both your money and your safety.

### The mix-up that costs people a day: Local vs Remote
The Desktop app's "New routine" button offers a choice of **Remote** or **Local**, and the names trip up many first attempts. **Remote** creates the actual cloud Routine this appendix is about — it runs on Anthropic's servers, laptop closed. **Local** creates a *different* feature, a Desktop scheduled task, which runs against your real files (including unsaved changes) but only while your machine is on. The practical workflow: prove a prompt works as a one-off run or Desktop task first, then promote it to a scheduled cloud Routine once it behaves.

### The two-routine gate, worked example
Because a Routine runs its prompt start to finish with no way to pause and ask you mid-run, a real approval gate has to sit *between* two Routines, not inside one. **Routine A** (the drafter) fires on a schedule and drafts the work — a `claude/` branch, a Slack summary, a draft email — without shipping it. **A human** reads the draft and decides. Only that approval fires **Routine B** (the executor) through its API trigger — a POST to its `/fire` endpoint with a bearer token that's shown exactly once, so it must be stored immediately. Routine B then performs the actual action: send, merge, deploy, pay. This is the same human gate from the main loop-engineering course, just built entirely out of Routine primitives and a webhook.

## Why would this be on the exam?
Routines are the easiest way many students first experience true unattended loops. The exam expects familiarity with the practical controls and safety features.
