# 22. Part 3 — Inform

## Simple Explanation (like you're 5)

A constrained agent that does not know what it needs to know will either fail or waste a lot of money guessing.

The “Inform” job of the harness is to give the agent the right information at the right time and in the right form.

This is also where **AX (agent experience)** lives — how pleasant and clear the world feels from the agent’s point of view.

## Key Concepts Unpacked

### Context surfaces as harness parts
Different kinds of knowledge belong in different places:
- Things that are always true → rules file (permanent instructions).
- Things that are true only for this kind of task → skill.
- Ability to reach outside systems → connector.

### Errors must say what to do next
A good error message is not just “it failed.” It tells the agent (or the human) the next concrete action to take. Bad error messages create doom loops where the agent keeps trying the same broken thing.

### AX (agent experience)
The agent’s version of user experience. Clear tool names, helpful error messages, stable identifiers, predictable structure, and good defaults all improve AX. Better AX means higher reliability and lower cost.

### The three surfaces as questions, and how to triage a bug
Each context surface answers exactly one question the harness must handle every beat: the **rules file** answers "what is always true here?" (conventions, boundaries — read every run, so keep it short since every line costs tokens every beat); **skills** answer "how do we do this specific job?" (loaded only when the task matches, so detail is free until needed); **connectors** answer "what can it reach, and how?" When a run fails because the agent *didn't know something*, this gives you a ten-second triage instead of an afternoon of prompt rewriting: always-true fact → rules file; task-specific knowledge → skill; missing reach → connector.

### AX's three concrete findings
Every surface has a reader, and it isn't you — it's the agent, mid-task, with no ability to ask what you meant. Three findings follow from designing for that reader: **fewer, focused tools beat many overlapping ones** (Anthropic's rule of thumb — if a human engineer can't say for certain which tool fits the job, neither can the agent); **tool descriptions do real work** ("searches the customer database by email or ID; returns at most 20 rows" beats "customer tool" the way a labeled door beats an unlabeled one); and **errors must say what to do next**, because in a loop the error message *is* the input to the next attempt — "Permission denied: request the `repo` scope" self-heals on the next beat, while a bare "Error 403" just wastes it. The test for any surface you write: could a competent stranger, seeing only this text, take the right next step?

## Why would this be on the exam?
A well-informed agent is dramatically cheaper and more reliable than a confused one. The exam expects you to know where different kinds of knowledge should live.
