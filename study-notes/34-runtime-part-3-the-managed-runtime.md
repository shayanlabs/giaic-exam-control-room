# 34. Part 3 — The Managed Runtime

## Simple Explanation (like you're 5)

A managed runtime is a service that gives you an agent, a safe environment, and a session without you having to run the computers yourself.

You gain convenience and isolation. You give up some control and you pay for the service.

## Key Concepts Unpacked

### Agent / environment / session
The three main objects the managed runtime gives you:
- **Agent**: the configured worker.
- **Environment**: the sandbox or container it runs inside.
- **Session**: one continuous run with its own memory and cost meter.

### What you get, what you give up, and what it costs
You get easy scaling, isolation, and less operational work. You give up deep control over the host and sometimes over exact tool versions. Cost is usually measured by active time.

### The self-hosted sandbox option
You can run a similar isolated environment yourself if you need more control or have compliance rules that a managed service cannot meet.

### About $0.08 per active session-hour; idle time is free
A concrete pricing example from the time of the course. The important idea is that you pay for active work, not for the mere existence of the configuration.

### The three objects, named precisely
The source's concrete example is Claude Managed Agents (public beta, April 2026). You create an **agent** (the definition: model, prompt, tools, guardrails — your rules file translated into a form a service can hold), an **environment** (the walled space where actions execute — a cloud sandbox by default, or a self-hosted sandbox on your own infrastructure when custody demands it), and a **session** (one ongoing piece of work with preserved state and an append-only event log, which can pause and resume across days since no laptop needs to stay open). The key architectural point the source makes: this is the moment the model that thinks and the sandbox that acts become visible as separate pieces, connected by the service, instead of living together in one process the way they did on your laptop.

### What you give up, precisely
The source breaks this into three things, lightest to heaviest: **visibility** (you read the event log the service emits, not the machine itself), **custody** (your prompts and data execute on infrastructure you don't control — a deciding factor for some data under some regulators, no feature list changes that), and **portability** (your definition is written in the vendor's shapes, so leaving means rewriting, not moving). On cost, the source gives a concrete figure as of when it was written: about eight cents per hour of *active* session work, with idle time free — meaning a session that thinks briefly and sleeps long is nearly free to keep, but a loop that wanders now wastes money as well as time.

## Why would this be on the exam?
Most production loops will live in some form of managed runtime. Understanding the trade-offs and the cost model is required.
