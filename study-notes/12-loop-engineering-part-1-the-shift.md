# 12. Part 1 — The Shift

## Simple Explanation (like you're 5)

For a couple of years the way we used coding agents was simple:
You type an instruction → the agent does one thing → you type the next instruction.

You were the boss on every single turn.

A **loop** changes that. You build a little system that can start work by itself, check the result, write down what happened, and decide what to do next. The system prompts the agent for you.

Your job does not disappear. It moves to the two things a loop can never do for you:
1. Saying clearly what you want (intent).
2. Being responsible for what ships (accountability).

## Key Concepts Unpacked

### Prompting vs looping
Prompting = you are in the driver’s seat every turn.
Looping = you design the car so it can drive itself for stretches of the road.

### The 6 parts of a loop
A complete loop has six pieces. Four of them form the working layers: the prompt, the context, the harness, and the loop itself. The fifth is the body of work. The sixth is the **spine** — the memory that connects one run to the next.

### Two roads
There are two main ways to build the same shape of loop. Claude Code gives you more of the loop machinery ready-made. OpenCode gives you the worker and you connect the rest yourself. The shape stays the same.

### Small loop vs big loop
A small loop is tight and fast (often inside one session). A big loop runs longer, across many sessions or on a schedule, and needs a stronger memory (spine).

### The spine is the 6th part
Without memory that survives from one run to the next, you do not really have a loop. You just have a series of separate prompts that keep forgetting what already happened.

### The four-layer stack, and why your prompt matters less now
The industry moved through four layers of engineering, roughly a year apart: first **prompt engineering** (the words you send), then **context engineering** (everything the model sees in one turn), then **harness engineering** (the code around the model that runs tools and handles errors — this is where the small loop lives), and now **loop engineering** (the outer cycle: what the system works on, when it starts, how it knows it's done). Each layer wraps the one before it, like nested boxes, and each layer stops a *different* kind of failure — a better prompt fixes only the prompt, but no prompt can rescue missing context, a missing checker, or a schedule that is still you. That's why a great prompt alone can no longer carry a whole system: it's just one input into a much bigger stack.

### The small loop's blind spot
Inside every agent sits a tiny "small loop": send context to the model, run any tools it asks for, feed the results back, repeat — in code, barely more than `while True: reply = model(context); if not reply.tool_calls: break`. Notice that `break` line: the small loop stops the moment **the model itself decides it's done**. Nothing checks whether the model is *right*. A common failure is the agent editing a file, writing "Done! All fixed," and stopping — without ever running the tests. This is exactly why loop engineering insists on **outside stops** that don't depend on the model's own opinion: a checked condition (a real test), a limit (max tries), a no-progress check, or a separate checker agent.

## Why would this be on the exam?
The shift from “I prompt” to “I design the system that prompts” is the biggest skill change in the whole course. Everything later assumes you understand this shift.
