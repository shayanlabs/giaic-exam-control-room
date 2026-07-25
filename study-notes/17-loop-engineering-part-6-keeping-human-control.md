# 17. Part 6 — Keeping Human Control

## Simple Explanation (like you're 5)

A loop that runs by itself is powerful. A loop that runs by itself with no human control is dangerous.

This part is about the feedback loops, the money reality, and the design choices that keep a human in charge even when the computer is working while you sleep.

## Key Concepts Unpacked

### Three feedback loops
Different levels of human involvement that keep the system honest and pointed at the right goals.

### Token cost and cadence
How often the loop runs has a huge effect on cost. The same design can cost about $20 per month or about $1,800 per month depending on how often it wakes up and how much context it loads each time.

### Human in / on / out of the loop
- **In the loop**: a human is required on every important step.
- **On the loop**: a human sets the goals and reviews the results but does not drive every turn.
- **Out of the loop**: the system runs with standing permissions and only calls a human for exceptions.

### AI gravity
The natural pull of a successful system to take on more and more work. Useful when you choose it on purpose. Dangerous when it grows without anyone deciding.

### Ng’s context advantage
Andrew Ng’s observation that the side with better context (data, process knowledge, evaluation) has a lasting advantage. Good spines and standing permissions are ways of putting that idea into practice.

### Standing permissions
Actions the loop is pre-approved to take without asking every time. They must be chosen carefully and reviewed from time to time.

### Three loops, three speeds — a worked example
Say you ask an agent to build a small typing game for a child. The **coding loop** turns in minutes: the agent writes the game, tests it, fixes bugs until it matches your instructions — this is the loop you build with this course's six parts. The **feedback loop** turns in hours: you open the game, try it, decide the buttons should be bigger or add unlockable costumes, then update your instructions and the agent builds again. The **outside loop** turns in days: real people — a friend, a child — actually use the game, and what they do shows you what to fix next. The loops nest inside each other, and the fast loop runs by itself while the two slow loops need you — because, as Andrew Ng puts it, you have a **context advantage**: you know who will use this and what "good" feels like, and the agent does not.

### In, on, or out of the loop — the industry's exact words
Beyond this course's "human gate," the wider world (AI safety papers, the EU AI Act, bank compliance teams) uses three fixed terms for the same idea, and a regulator or buyer will use them precisely: **human in the loop** means a person approves each action before it takes effect (higher control, slower — this is prompting turn by turn, or the human gate itself); **human on the loop** means the system acts on its own while a person watches and can step in (a Routine pushing to `claude/` branches while you review each morning); **human out of the loop** means nobody is watching and nobody can intervene — this is never presented as a third valid option, it's the failure mode. A good loop mixes these per action: the morning-triage loop runs on-the-loop for safe fixes and drops back in-the-loop for anything risky, like the reviewer's FAIL or the final merge to `main`.

## Why would this be on the exam?
The exam is not only about making loops that run. It is about making loops that stay safe, affordable, and under human control.
