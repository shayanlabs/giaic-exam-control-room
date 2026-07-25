# 39. Part 3 — Working Unwatched

## Simple Explanation (like you're 5)

This is the point of the whole stack: the agent can do useful work while no device of yours is online.

The design pattern is a clear delegation loop with scheduled execution and explicit reporting.

## Key Concepts Unpacked

### The delegation loop
brief → plan → approve → review

You give a clear brief, the system proposes a plan, you approve, the work happens, and you review the result. Skipping any step increases risk.

### Scheduled tasks with no device online
The technical reality that the session lives on the vendor’s servers and can fire on a schedule even if every laptop and phone you own is off.

### The 4 answers of a schedule
A good schedule configuration answers: when it runs, what it is allowed to do, how it reports, and what happens on failure.

### Reporting vs acting
There is a big difference between an agent that only produces a report for a human and an agent that is allowed to take actions in the world. The permission boundary must be explicit.

### Why the plan step is the real safety net
On a desktop agent you can often watch the work run and interrupt mid-step. On the web surface you walk away — that's the whole point — so the plan is usually your *only* intercept between intent and finished work. Skip the "lay out your plan first, and pause for my approval" line, and your first chance to catch a mistake comes after it has already run across every file in the task. When you do review a plan, four checks take about two minutes: is the scope only what you named, does anything act before it verifies, is it reaching for a connector or send you didn't ask for, and what is it silently assuming about format or audience? A one-sentence redirect at the plan stage costs nothing; cleaning up a confidently executed wrong run costs an afternoon.

### The invoicing example: reporting vs acting, made concrete
Say Ayesha wants two scheduled tasks: a Monday-morning summary of unpaid invoices (read from Drive, brief saved to her account), and an automatic Friday task that emails payment reminders to every late client. The Monday summary is a reporting schedule — read, synthesize, land the file — and a wrong week just costs a rewrite. The Friday reminders *act* on the outside world unattended, on a cadence, and a wrong run emails real clients with nothing checking the work before it goes out. The one-word difference between what's safe now and what must wait for deeper tooling (a checker, a stopping condition, saved state) is **acting** versus reporting.

## Why would this be on the exam?
True unattended work is the economic and practical justification for everything else in the course. The exam expects you to understand the delegation pattern and the safety boundaries.
