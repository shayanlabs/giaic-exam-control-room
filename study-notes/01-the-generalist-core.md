# 1. The Intent Bottleneck and the Generalist Core

## Simple Explanation (like you're 5)

Imagine a big kitchen.

For a long time, one boss told 8 cooks what to make. Cooking took a long time by hand, so the boss had plenty of time to explain each dish carefully.

Then someone invented magic ovens and robot helpers. Each cook can now finish 5 times more food — and the robots also handle a lot of the routine watching-over that used to take up the boss's time. Because the boss no longer has to babysit the actual cooking, one boss can now be responsible for 20 cooks instead of 8.

But here's the catch: the boss still has to decide *what* every single one of those cooks should make — and now there are 20 menus to plan instead of 8. Cooking got faster. Deciding did not. So deciding is now the slow part of the kitchen.

That's what happened when coding agents arrived. Building software became fast. Deciding *what* to build and explaining it clearly became the new slow part. People call this the **intent bottleneck**.

## The Generalist Core

Four jobs that work together like a team:

1. **Decide what the AI should do** — owns the intent
2. **Build the AI worker** — turns intent into a working system
3. **Design the company that runs many AI workers** — the org-level architecture
4. **Keep everything running on real computers** — production and reliability

When one person does all four jobs inside a customer's company, the market calls that person a **Forward Deployed Engineer (FDE)**.

## Key Concepts Unpacked

### The intent bottleneck
- Old ratio: about 1 product manager for every 8 engineers.
- New ratio: about 1 product manager for every 20 engineers.
- **Why the ratio changed:** agents let each engineer build much faster and need less hands-on oversight, so one PM can now be responsible for more engineers.
- **Why that creates a bottleneck:** even covering more engineers, the PM still has to decide and clearly explain what every one of them (and their AI agents) should build. That deciding work didn't get any faster — so it becomes the new traffic jam. This is why the first role, Outcome Architect, matters so much.

### Outcome Architect
Owns the "what" and the "why." Doesn't build the AI. Writes clear instructions covering:
- What the AI worker should achieve
- What "good enough" looks like
- Which workers should be built first

Think of them as the person who writes the recipe card before anyone starts cooking.

### Digital FTE Builder
"FTE" means Full-Time Equivalent — basically, one full-time human worker. A **Digital FTE** is an AI worker that can do a job a human used to do. This person takes the clear instructions from the Outcome Architect and actually builds the AI worker. This is the primary role this material trains you for.

### AI-Native Co. Architect
Designs the whole company that runs on many Digital FTEs — deciding how the AI workers talk to each other, how humans stay in control, and how success gets measured.

### Cloud AI Engineer
Keeps the AI workers running on real cloud infrastructure day and night. Building is only half the job; keeping it alive and reliable is the other half.

### The 4-role pipeline
A clean hand-off: **Intent → Build → Design the company → Run it in production.**

## The Bigger Question Behind This Topic

Historian Yuval Noah Harari has raised a challenge educators can't easily answer: for perhaps the first time, nobody can say with confidence what jobs will exist in ten years — so nobody knows exactly what to teach today. The old safe answer was "learn to code." That answer is weakening, because AI is getting rapidly better at writing code — some predict it may write most code better than most humans within the next year or so.

This material's answer: don't just train people to write syntax. Train people to work *above* the machine — the ones who decide what to build, supervise the AI workers doing the building, and verify what comes back. Syntax can be automated. Judgment, specification, and deployment are much harder to automate — and as AI gets more capable, the value shifts even further toward these human judgment calls, rather than shrinking. Each of the four generalist-core roles is a seat at that level.

## Why This Might Be on the Exam
Almost every later topic in the course lives inside one of these four roles. Without understanding this pipeline and the intent bottleneck, the rest of the material can feel like disconnected pieces.
