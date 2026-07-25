# 31. Parts 5 + 6 — The 12-case suite and staying honest

## Simple Explanation (like you're 5)

Even a good evaluation system can be gamed or can give false confidence.

These final parts cover a practical 12-case pattern and the honesty habits that keep you from fooling yourself.

## Key Concepts Unpacked

### Goodhart’s law
When a measure becomes a target, it stops being a good measure. If the team only optimizes for the golden-set score, the score stops reflecting real-world quality.

### Hold-outs
Cases that the development process is not allowed to train or tune against. They are the last line of defense against self-deception.

### What evals cannot prove
Evals can show that certain known failure modes are absent. They cannot prove the system is safe in every possible future situation. Knowing the limits is part of honesty.

### The injection category bar means all of them must pass
For security-sensitive categories (prompt injection and similar), the bar is usually “all must pass,” not “the average score is high.” One failure is a real risk.

### Attack fixtures are live ammunition
The cases that test for injection and other attacks are dangerous if they leak or are mishandled. Treat them with the same care as real exploits.

### A worked example: the Goodhart gap
Picture a team tuning their suite for two months until it hits a perfect 36/36 — but their sealed hold-outs, which were never tuned against, have quietly slipped from 90% down to 70%. Nothing malicious happened; every small prompt and rule tweak was validated against the same 36 verdicts, so the system slowly learned the test instead of the material. The source's fix is two moves: promote some hold-outs into the tuned set since they now represent reality better than the memorized cases, and refresh the stalest low-severity cases from recent production failures — then re-baseline and seal a fresh batch of hold-outs.

### Never let the agent see the answer key
Beyond keeping fixtures physically dangerous (real attack text that can steer a session that wanders into that folder), the source adds a second, easy-to-miss reason to keep the fixtures folder out of everyday context: the reviewer may be *tested* on a case like `deleted-test-001`, but it must never be able to *read* it. A deny rule blocking reads of that folder outside of eval runs is the one-line fence the source recommends for turning that habit into a wall.

## Why would this be on the exam?
The final honesty layer is what separates a professional evaluation practice from a score-chasing exercise. The exam expects you to know both the techniques and their limits.
