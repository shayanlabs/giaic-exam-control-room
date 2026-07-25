# 14. Part 3 — The Body

## Simple Explanation (like you're 5)

The body is the part that actually does the work inside one run of the loop.

If the heartbeat is the alarm clock, the body is the person who gets up and does the chores.

## Key Concepts Unpacked

### Worktrees
Separate folders and branches so two agents (or two runs) do not step on each other’s files and create a mess.

### Skills
Saved packets of instructions that an agent can reuse. They package knowledge and preferred ways of working.

### Connectors
The pipes that let the agent reach outside systems (GitHub, Slack, databases, etc.).

### Maker–checker
One agent (or process) creates the work. A different agent or command checks it. This is one of the most important reliability patterns. Never let the same process both make and fully approve its own work when the stakes are high.

### The checker ladder
A set of checks that get stronger and more expensive. Start with cheap/fast checks. Only use expensive/thorough checks when needed.

### Dynamic workflows are the body of one beat, not a loop
A fancy multi-step workflow inside a single run is still just the body. The loop is the thing that decides to start another run later.

### Verification skills across 4 homes
The checking logic can live in different places depending on the tool: rules files, skills, hooks, or outside checkers.

### Why connectors need special rules in a loop
A connector (built on MCP) is what lets a loop *act* instead of just talk — open a PR, update a ticket, post to Slack. But because a loop retries and picks tools with nobody watching, three rules matter that don't matter as much by hand: **fewer, focused tools beat many overlapping ones** (a tool choice is a decision made fresh every beat, with nobody checking it — if a human engineer can't say for certain which tool fits, neither can the agent); **writes must be safe to repeat** (a retried "create customer" call that makes a second customer means duplicate billing, so prefer update-or-create over blind creates); and **error messages must say what to do next**, because in a loop the error message *is* the input to the next beat — "Permission denied: request the `repo` scope" fixes itself on retry, while "Error 403" just wastes a beat.

### The four homes of a verification skill
A check you keep running by hand after every change ("did I strip the request body from the logs?") can live in one of four homes, each a different heartbeat: **standalone** (you invoke it deliberately — you're still the heartbeat), **embedded** (appended to the end of the skill that does the work, so it fires automatically — but only works on skills you can edit, since built-in or plugin skills get silently overwritten), **chained** (one skill calls the next at its end, turning "I always run the check after" into "the skill always runs the check"), and **on every PR** (the same check fires through the event heartbeat, so a teammate's change passes the same gate yours did). The graduation rule: don't jump straight to "on every PR" — a check earns each home by proving itself right in the one before, the same "watched before unattended" discipline that governs loops themselves.

## Why would this be on the exam?
Most of the concrete engineering work of building loops lives in the body. The exam expects you to know the main pieces and especially the maker–checker idea.
