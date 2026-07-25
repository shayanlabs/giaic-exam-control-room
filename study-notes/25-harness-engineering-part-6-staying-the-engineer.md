# 25. Part 6 — Staying the Engineer

## Simple Explanation (like you're 5)

Building a harness is only half the job. Keeping the harness healthy for months and years is the other half.

A harness that is never cleaned becomes a junk drawer of old rules. It slows the agent down and creates surprising bugs.

## Key Concepts Unpacked

### Observability
You cannot improve what you cannot see. You need logs, traces, and numbers about what the agent and the harness actually did.

### The capability–control trade-off
More power usually means less control (and the other way around). Every design choice sits somewhere on this line. The goal is to choose the point on purpose, not to maximize power.

### Harness coupling
How tightly the harness is tied to the exact behavior of today’s model or tools. Tight coupling makes the harness break when models or tools change.

### Rule debt
The pile of old, overlapping, or obsolete rules. It makes the agent slower and the system harder to understand.

### Couple to contracts, not behaviors
Prefer stable success criteria and interfaces over “do it exactly the way model X currently does it.”

### The 90-day rule for retiring rules
A practical hygiene habit: every rule should be looked at again after about 90 days and either re-justified or removed. This prevents permanent rule debt.

### Three forces that push back on the ratchet
The ratchet only turns one way — tighter — and that's also its danger. Three forces hold it in check. The **capability–control trade-off**: every rule that removes a failure also removes a move, so a harness at maximum tightness produces work at minimum ambition — overnight loops on real repos run tight, a throwaway prototype session runs loose, and the craft is placing most work correctly in between. **Harness coupling**: a harness tuned too closely to one model's odd habits quietly becomes part of that model — a real example is a new model generation producing about 30% more tokens for the same text, which silently breaks every token budget measured on the old model. The defense is coupling to *contracts* (exit codes, schemas, tests) rather than to one model's *behavior*. **Rule debt**: every rules-file line costs tokens every beat, every hook costs seconds every action — a one-time oddity that earns a permanent rule isn't safety, it's junk, so review the rule set monthly and treat any rule that hasn't fired in 90 days with no linked incident as a candidate for removal (walls around secrets are the one exception, always safe from this pruning).

### When to stop configuring and start building your own
Stay with a vendor harness (Claude Code, OpenCode) as long as its surfaces can express your rules — that's most people, most of the time, and the vendor's harness improves weekly for free. You build your own harness only when the product's walls block a requirement you actually have: your own tool interface, your own verification stack, your own deployment shape. That's the threshold into the book's Mode 2 material — Build AI Agents, Eval-Driven Development, and Deploy the Agent Harness — which is the same five verbs (constrain, inform, verify, correct, escalate), just written in more code instead of configured through a settings file.

## Why would this be on the exam?
Building a harness is only half the work. Keeping it healthy is the other half. The exam expects you to know the long-term maintenance habits.
