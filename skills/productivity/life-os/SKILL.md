---
name: life-os
description: Run the user's everyday operating system in Notion, split into a Work area and a Personal area — capture tasks, projects, files, and the results of tasks and conversations, but write to Notion only with the user's explicit permission. Use when the user wants to save, log, file, capture, or remember something "in Notion", "in my OS", "for work", or "for personal"; asks what's on their plate, what they saved, or to review their week; or when a task or conversation produces a result worth keeping.
---

# Life OS

The user's everyday operating system lives in Notion, split into two **areas**: **Work** and **Personal**. You keep it current — but Notion is theirs, so **nothing is written without their permission**. Reading to answer a question is fine; every create, update, move, or archive is proposed first and happens only on a yes.

## Notion capability mapping

The body below is written in capabilities. The Notion connector's tool names sit here, once, so a rename is a one-line change. This mapping is deliberate and load-bearing — check it against the connector's tool list when a call fails.

| Capability | Notion connector tool |
|---|---|
| search | `notion-search` |
| read page or database | `notion-fetch` |
| create pages or database rows | `notion-create-pages` |
| update page properties or content | `notion-update-page` |
| create database | `notion-create-database` |
| move pages | `notion-move-pages` |

No Notion connector in the session? Stop and say so: the user has to connect Notion before this skill can do anything. Don't fall back to writing local files as if they were the OS.

## The structure

```
Life OS                      (root page)
├── Work                     (area page)
│   ├── Projects             (database)
│   ├── Tasks                (database)
│   └── Records              (database)
└── Personal                 (area page)
    ├── Projects
    ├── Tasks
    └── Records
```

Each area owns its own databases rather than sharing one with an `Area` property. The split is physical, so a Work page can be shared with colleagues without ever exposing a Personal row, and a misfiled item is one move away from correct.

Database properties are identical across both areas:

- **Projects** — `Name` (title), `Status` (Active / Paused / Done), `Goal` (text), `Due` (date).
- **Tasks** — `Name` (title), `Status` (Inbox / Next / Doing / Waiting / Done), `Due` (date), `Project` (relation → that area's Projects).
- **Records** — `Name` (title), `Type` (Result / Conversation / File / Note / Decision), `Date` (date), `Project` (relation → that area's Projects), `Source` (text: where it came from — a session, a URL, a file name). The page body holds the content itself.

**Records** is where the results of tasks and conversations go. A Record is the durable output — the answer, the decision, the drafted text, the summary of what was settled — not a transcript.

## First run: find or build the OS

1. **Search** for a page titled `Life OS`. If it exists, read it and its two area pages to learn the database IDs, and carry on. Trust the structure you find over the one above; if the user has renamed or added properties, use theirs.
2. If it doesn't exist, show the user the tree above and ask where to create it (a parent page, or the workspace top level). Build it only on a yes, then report the link.

Never create a second `Life OS` because the first search came back thin — search again with the area names before concluding it's missing.

## The permission gate

Every write passes through one gate. Before writing, show a **save proposal**:

```
📥 Save to Notion?
Area:     Work
Where:    Records
Title:    Q3 pricing decision
Type:     Decision · Project: Pricing revamp
Content:  <the first lines, or a one-line summary of what the body will hold>

Reply: yes · edit · personal (switch area) · skip
```

Then wait. A yes covers exactly the proposal shown — not similar items later.

The user may widen permission in their own words — "save all the results from this session to Work", "you can always log tasks I mention". Honour exactly what they said, for as long as they said it (this session unless they said otherwise), and still announce each write as you make it so they can veto it. Permission never carries across into the other area, and never carries across sessions unless the user says so in that session.

Batch where it's natural: at the end of a conversation that produced several keepers, offer them as one numbered list and let the user pick by number.

## Choosing the area

Propose the area; never silently decide it.

- Clear signals (employer, colleague, client, a work repo → Work; family, health, money, home, hobbies → Personal) let you propose with confidence.
- Ambiguous items — a learning goal, a side project, a book — get the question asked, not a guess.
- When in doubt, Personal is the safer default for anything private: misfiling personal into Work is the error that leaks.

## What to capture, and when

| Moment | What you offer |
|---|---|
| The user mentions something they need to do | A **Task** in that area's Inbox |
| A task in this session finishes with an output worth keeping | A **Record** of type Result, linked to its project if one fits |
| A conversation settles a decision or produces a plan | A **Record** of type Decision or Conversation — the outcome and its reasons, not the back-and-forth |
| The user shares or produces a file | A **Record** of type File. Put the file's text in the body when it's text; for binaries, record what it is and where it lives, and attach it only if the connector supports uploads |
| A new multi-step goal appears | A **Project**, with its first Tasks |

Offer, don't nag. One offer per keeper, at the point it's finished — not after every message, and not again once the user has skipped it.

## Reading the OS

Answer questions from Notion freely: "what's on my plate at work?", "what did we decide about the pricing?", "what did I save last week?". Read only the area the question is about. For a review ("plan my week", "weekly review"), read both areas' Tasks and active Projects, present them grouped by area, and propose any status changes as one batch through the gate.

## Content rules

- **Redact secrets** — API keys, passwords, tokens, account numbers — before proposing a save, and say that you did.
- **Summaries over transcripts.** Store what the user will want when they come back: the result, the decision and its reasons, next steps, and links to primary material.
- **Update rather than duplicate.** Search the target database for an existing page before proposing a new one; if one fits, propose an update to it instead.
- **Never delete.** Archiving or deleting is proposed like any other write, and only when the user asks for it.
