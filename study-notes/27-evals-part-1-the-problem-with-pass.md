# 27. Part 1 — The Problem with PASS

## Simple Explanation (like you're 5)

A normal test asks: “Is the answer exactly this string?”
An **eval** asks: “Is the work actually good enough for the real purpose?”

Passing a test is not the same as being trustworthy.
Worse, the judge is often itself a language model, so it can have the same weaknesses as the system it is judging.

## Key Concepts Unpacked

### Test vs eval
- **Test**: exact match, brittle, usually yes/no.
- **Eval**: graded judgment against a rubric or success criteria. It can look at many dimensions at once.

### The 3 depths
You can judge at different levels:
- **Answer** — is the final output good?
- **Actions** — did it take the right steps?
- **Trace** — is the full reasoning and tool-use history sound?

### The judge is a model too
Therefore the judge can suffer from:
- **Leniency drift** — becomes more generous over time.
- **Self-preference** — prefers answers that look like its own style.
- **Surface bias** — is impressed by fluent language even when the substance is wrong.
- **Drift** — its own behavior changes when models or prompts are updated.

### A worked example: the depth that catches the hard fix
Imagine the agent "fixes" a failing test by hard-coding the expected value straight into the function instead of fixing the real bug. Depth 1 (the answer) says PASS — the tests are green. Only Depth 2 (the actions — reading the actual diff) shows a constant was written directly into the code under test, which is exactly the kind of failure an output-only eval will miss for a month. This is why the source names three depths on purpose: **answer**, **actions**, and **trace** — cheap cases only need depth 1, but the cases that actually protect you have to grade depth 2 or depth 3.

### Why one clean demo proves so little
The source points at the same compounding math from earlier in the curriculum: a loop whose steps each succeed 95% of the time only finishes a 20-step run cleanly about 36% of the time. A demo is one run, on a task picked because it demos well, watched by someone hoping it works — so a single clean demo can come from a system that fails most real tasks. That is the real distinction the note is making: demos persuade, evals inform, and you need both but should never confuse which is which.

## Why would this be on the exam?
“It passed” is one of the most dangerous phrases in agent development. The exam wants you to understand why a simple pass is not enough.
