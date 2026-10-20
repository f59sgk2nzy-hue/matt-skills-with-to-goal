---
name: life-os-dreaming
description: Review your Life OS in Notion and get at most four evidence-backed improvements — repeated work to turn into a skill, stale records, duplicated effort, idle projects.
argument-hint: "Work, Personal, or both"
disable-model-invocation: true
---

# Life OS Dreaming

Look across the whole Life OS the way no single conversation can, and return **at most four recommendations**, each with its evidence, a proposed action, and an estimated time saved. Recommend only: every change goes through the `/life-os` permission gate, so nothing is written to Notion without the user's yes.

Idea adapted from a public video demo of a self-improving "agentic OS" (https://www.youtube.com/watch?v=MAuLQzcMrS0). The demo shows a product, not its code, so the procedure below is an adaptation, not a copy of anyone's implementation.

## Before starting

Find the `Life OS` page (see `/life-os` for the structure). If it is missing, stop and say so. Ask which area to review — Work, Personal, or both. Never mix areas inside one recommendation; a finding that spans both is split or dropped.

## The dimensions

Score each against what Notion actually holds. A dimension with no evidence is skipped, never invented.

| Dimension | Looks for | Evidence in the OS |
|---|---|---|
| Repeated work | A manual task done three or more times → candidate skill | Similar Task or Record names in the last 7 days, clustered by intent |
| Stale memory | Records out of date or never revisited | Records not edited for 30+ days still marked current |
| Workflow patterns | The same research redone; stalled tasks | Duplicate Records; Tasks in Waiting or Doing past their due date |
| Idle outcomes | Projects going nowhere | Active Projects with no recent Task or Record activity |
| Skill performance | Skills never used | Records citing a skill, or the user's skills folder |
| Cost and session hygiene | Expensive models on simple work, long sessions | Not in Notion — hand off to the user's own usage pages |
| External opportunities | New skills or tools that fit | Web search, only if the user opts in |

## Procedure

1. **Read.** Take the chosen area's open Tasks, Active Projects, and the last 30 days of Records.
2. **Score.** Rate the dimensions that have evidence. Cluster similar items by intent, not by exact title.
3. **Ask once** whether web search for external opportunities is wanted.
4. **Pick four.** The highest-leverage findings only. Each carries the finding, its evidence (item names and links), the proposed action, and a time-saved estimate labelled as an estimate. If the user has said what an hour of their time is worth, show the value; otherwise show hours.
5. **Present** a numbered list. Nothing is written yet.
6. **Wait** for the user's reply by number: do, skip, or later.
7. **Act through the gate.** Each "do" becomes a save proposal under `/life-os`. A finding that becomes a skill is drafted as a `SKILL.md` and saved as a Record — never installed automatically.
8. **Hand off** the cost and session dimensions: tell the user what to check in their own usage pages and wait for their numbers.

## Rules

- Recommend, never act.
- At most four recommendations per run; a fifth waits for the next run.
- Every claim points at a specific item. A finding with no item behind it is dropped.
- Estimates are labelled as estimates.
- Fewer than about ten items in the window means too little data: say so and suggest running again later instead of padding the list.

## When the user returns

Find the last "Dream" Record in the area and review only what changed since its date. Save each run's accepted findings as a Record of type Note named "Dream — <date>" (through the gate) so the next run has a starting point.
