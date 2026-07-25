# 37. Part 1 — The Shift

## Simple Explanation (like you're 5)

The same web address can now host two completely different things:
- the old chat box that waits for you on every turn, and
- a remote session that can keep working after you close the tab.

That is the shift.

## Key Concepts Unpacked

### Same address, two different things
claude.ai or chatgpt.com can be either an interactive chat or a surface that hosts longer-running, schedulable agent sessions. You must know which one you are using.

### The remote session
A session that lives on the vendor’s servers and can continue (or be restarted) without your laptop or browser being open.

### Two vendors, one shape
Even though the products differ, the underlying shape of a general agent on the web is the same: heartbeat, connectors, run-until-done, spine, gate, body.

### The stop-typing test
A simple practical test: if the system stops when you stop typing and close the tab, you are still in the chat box. If it can continue, you are in the remote-session world.

### The 6 parts
The same six loop parts apply on the web surface. The implementation details change; the shape does not.

### The real line under the stop-typing test
A plain chat turn is *synchronous*: it runs while you wait, then stops and waits for your next turn. An agent run is *delegated*: once you start it, it keeps moving toward an outcome without needing your next turn to continue. There's a catch worth knowing — you can *start* a delegated run from inside the chat box, in plain words like "Every Monday, summarize these emails." The words go in the chat, but what you set up is a delegated task, not a normal reply. So the test isn't really about where you typed; it's about what the work *does* after you stop.

### A worked example: Ayesha's power cut
Ayesha in Lahore starts a client report in a web session at 5pm. Load-shedding cuts her power at 6. At 8pm she opens the session from her phone — and finds the work finished, or waiting at an approval for her to clear. Her power was never the problem, because the session ran on the vendor's servers the whole time; her laptop was only ever a window onto it, and a closed window doesn't stop what's on the other side of it. Contrast this with a desktop agent (met in a later course), which would have paused the instant her machine lost power, because there the machine *is* the runtime.

### Reading a new product with the six parts
The six parts aren't just theory — they're a decoder ring for marketing pages. When a vendor advertises "Triggers," that's the heartbeat. "Integrations" are connectors. "Autopilot mode" is the run-until-done loop (and your first question for the docs should be: what is the stopping condition, and who checks it?). "Workspace memory" is the state spine. Reading an unfamiliar product's feature list through this lens lets you place it inside the same six-part shape in under a minute, no matter which company built it.

## Why would this be on the exam?
Web agents are the most accessible surface for many users. The exam expects you to understand how the loop ideas map onto this surface.
