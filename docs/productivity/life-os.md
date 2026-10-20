## What it does

`life-os` runs your everyday operating system in Notion, split into two **areas** — **Work** and **Personal**. Each area has its own Projects, Tasks, and Records, and Records is where the results of tasks and conversations land: the answer, the decision and its reasons, the drafted text, the file.

Nothing is written to Notion without your say-so. Every create, update, or move goes through a **permission gate**: the agent shows you a save proposal — area, database, title, a preview of the content — and waits for a yes. Reading your OS to answer a question needs no gate; changing it always does.

## When to reach for it

Type `/life-os`, or the [agent](https://www.aihero.dev/ai-coding-dictionary/agent) reaches for it automatically when a task fits — you mention something you need to do, a conversation settles a decision, or a task finishes with an output worth keeping.

| Situation | What happens |
| --- | --- |
| "Remind me to renew the passport" | A Task proposed in Personal's Inbox |
| A task in the session finishes with a result | A Result record proposed, linked to its project |
| A conversation settles a plan | A Decision record with the outcome and why — not the transcript |
| You share a file | A File record, with the text in the body when it is text |
| "What's on my plate at work?" / "Weekly review" | Read straight from Notion; status changes proposed as one batch |

## Prerequisites

A Notion connector connected to the session the skill runs in. On first run the skill searches for a page called `Life OS`; if there isn't one, it shows you the structure and asks where to build it. It builds nothing until you say yes.

## Two areas, physically separate

The split between Work and Personal is a separate set of databases per area, not a tag on one shared set. That is what lets you share your Work area with colleagues without a Personal row ever being one filter away from them. The agent proposes the area for every item, asks when the item is ambiguous, and falls back to Personal for anything private — filing personal things under Work is the mistake that leaks.

## The gate, and how to widen it

A yes covers the one proposal in front of you. When that gets tedious, widen it in your own words — "save every result from this session to Work", "always log tasks I mention". The agent honours exactly that scope, for this session unless you say otherwise, and still announces each write so you can veto it. A widened permission never crosses into the other area.

## Common questions

**Will it save my whole conversation?**
No. A Record holds what you'll want when you come back — the result, the decision and its reasons, next steps, links to primary material. Transcripts are noise in a system you mean to reread.

**What about passwords or keys that came up?**
They are redacted before the proposal is shown, and the proposal says so.

**I already have a Notion setup. Will it fight mine?**
If a `Life OS` page exists, the skill reads the structure it finds and uses your properties over its defaults. Keep the root page name, and it will find it.

## It's working if

- Nothing appears in Notion that you didn't see a proposal for — or explicitly pre-approve.
- Work items never show up in Personal, and the reverse.
- Coming back a week later, a Record tells you what was decided without reopening the conversation.
- The agent offers a save once per finished keeper, and stops offering after you skip.

## Where it fits

`life-os` is a **reach-for-it-anytime standalone** that sits beside every other skill rather than inside a chain: whatever another skill produces — a spec from [to-spec](https://aihero.dev/skills-to-spec), a cited report from [research](https://aihero.dev/skills-research) — can become a Record in the right area. [ask-matt](https://aihero.dev/skills-ask-matt) routes over the whole set.
