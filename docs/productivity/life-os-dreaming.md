## What it does

`life-os-dreaming` is a periodic look-back over your Life OS in Notion. It reads one area's open Tasks, Active Projects and the last month of Records, and returns **at most four recommendations** — each with the evidence behind it, a proposed action and an estimated time saved.

It recommends and never acts. Every change it proposes goes through the permission gate of [life-os](https://github.com/tt-a1i/matt-skills-with-to-goal/blob/main/skills/productivity/life-os/SKILL.md), so nothing is written to Notion without your yes.

## When to reach for it

You invoke this by typing `/life-os-dreaming` — the agent won't reach for it on its own, because you decide when to look back.

| Situation | Why now |
| --- | --- |
| End of the week or month | The Records have piled up and nobody has reread them |
| You keep doing the same chore by hand | Repeated work is the first thing it looks for |
| The OS feels cluttered | Stale records and idle projects are two of its dimensions |

Pass `Work`, `Personal` or `both` to choose the area; a finding never mixes the two.

## Prerequisites

A `Life OS` page in Notion with Work and Personal areas, as set up by [life-os](https://github.com/tt-a1i/matt-skills-with-to-goal/blob/main/skills/productivity/life-os/SKILL.md). It writes only through that skill's gate, and saves each run's accepted findings as a Record named "Dream — <date>" so the next run starts where this one stopped.

## Four, with evidence

The leading word is the cap: **four recommendations, each pointing at specific items**. A finding with no item behind it is dropped, and a fifth waits for the next run. The dimensions it scores are repeated work (the same chore three or more times becomes a candidate [skill](https://www.aihero.dev/ai-coding-dictionary/skill)), stale memory, workflow patterns, idle outcomes, skill performance, and optionally external opportunities from a web search. Cost and session hygiene need usage data Notion doesn't hold, so those are handed back to you to check.

## Common questions

**Does it work without much data?**
Not well. With fewer than about ten items in the window it says so and suggests running again later, rather than padding the list.

**Where do the time-saved numbers come from?**
They are estimates and labelled as such. If you tell it what an hour of your time is worth, it shows the value as well as the hours.

## It's working if

- Each recommendation names the Tasks or Records behind it.
- You get four items or fewer, never a long list.
- Nothing in Notion changes until you reply by number.
- Running it twice in a row doesn't repeat findings you already accepted.

## Where it fits

`life-os-dreaming` is a **reach-for-it-periodically standalone** that sits on top of [life-os](https://github.com/tt-a1i/matt-skills-with-to-goal/blob/main/skills/productivity/life-os/SKILL.md): life-os fills the OS, this reviews it. A finding that is a repeated task can become a new skill, drafted and saved as a Record rather than installed. [ask-matt](https://aihero.dev/skills-ask-matt) routes over the whole set.
