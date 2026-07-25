# 36. Parts 5 + 6 — Choosing a home

## Simple Explanation (like you're 5)

There is no single best home for every loop.

The right choice depends on who the user is, what you must own, whether a human is waiting, and what a bad night would cost. You can also mix homes.

## Key Concepts Unpacked

### The four questions
1. **Who is the user?** (developer, end-user, internal ops, external customer…)
2. **What must you own?** (data, credentials, the model, the logs, the ability to switch vendors…)
3. **Does a person wait?** (interactive vs fully unattended)
4. **What does a bad night cost?** (money, reputation, safety, compliance…)

### Mixing homes
It is normal and often wise to run different parts of a system in different homes (development on laptop, scheduled work in cloud, sensitive execution in a locked-down environment).

### Lock-in as a rate
Vendor lock-in is not a yes/no question. It is a rate: how expensive and slow is it to leave? Design so that rate stays acceptable.

### Ownership drift
The slow, almost invisible loss of control that happens when more and more critical pieces live inside a vendor’s black box. Periodic review is the defense.

### A worked example: when even Home 3 isn't enough
The source pushes Ayesha's invoicing loop (from Part 2) further: she now serves five clients, one a bank requiring client data to stay on infrastructure her firm controls. Q1 (other people depend on it) rules out Home 1. Q2 is the deciding question — the bank's "must" is about execution and data, which a managed control plane with a **self-hosted sandbox** can satisfy by keeping data in the firm's custody while a vendor still operates the loop; but if the requirement reaches the control plane itself (the prompts, sessions, model path), only an owned runtime answers it. The source's honest conclusion: this is precisely the edge where an operator configuring tools alone isn't enough anymore — it's where Mode 2 (building custom agent infrastructure) begins.

### Lock-in is a rate, not a yes/no event
The source is specific that lock-in leaks rather than getting signed away: a rule tweaked only in a vendor-side setting and never mirrored to the repo, an eval case added only inside a service console, a bar renegotiated in a dashboard with no commit behind it. Each is one item quietly moving out of the suitcase. The source's concrete test for measuring it: periodically try to configure a fresh home from the repo alone — if that fresh build can't be completed, you've found the leak while it's still small. Ownership drift is the quieter companion problem: a home that runs quietly for months tempts you to stop reading the per-category reports, which is why the defense is a calendar reminder to actually read them, not just a dashboard that exists.

## Why would this be on the exam?
Choosing the wrong home is expensive and sometimes hard to reverse in the short term. The exam expects you to have a decision framework, not just a favorite tool.
