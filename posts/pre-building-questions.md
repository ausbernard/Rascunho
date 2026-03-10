---
title: Partida - First Principles
date: 2026-03-02
author: Berny
category: Design
excerpt: "Questions to ask before building the next project"
---

## The Comfort Zone Trap

*Before I can make better choices, I have to admit what my default instincts are.*

**Questions to answer:**
- What did I almost build Partida with?
- What's my "default stack" and where did it come from?
- When have I chosen familiarity over fit before—on this project or past ones?

---

## The First Principle Questions

*Before writing a single line of code, I forced myself to answer:*

- What does this app actually *need* to do? (Not features—*capabilities*. What must it be capable of?)
- Who's using it? Just me? My family? Other families eventually?
- What constraints actually matter? (Speed to ship? Maintainability? Portability? Fun?)
- What don't I know that I don't know?

---

## The Contenders

*The options I seriously evaluated—not just the ones I already knew.*

**Questions to answer:**
- What 2-3 stacks did I consider?
- What made me look beyond my comfort zone?
- What did Claude suggest that surprised me?
- Did I prototype anything just to test an assumption?

---

## The Trade-Off Table

| Stack Option | Learning Curve | Dev Speed | Maintainability | Fun Factor |
|--------------|----------------|-----------|-----------------|------------|
| Option 1     |                |           |                 |            |
| Option 2     |                |           |                 |            |
| Option 3     |                |           |                 |            |

**Questions to answer:**
- What won in each category?
- What did I have to give up to get what I wanted?
- Which trade-off was hardest to accept?

---

## Why I Landed Here

*My final stack—and why each piece earned its spot.*

- **HTMX**: Why HTML fragments over JSON?
- **FastAPI**: What made me stick with Python?
- **AlchemySQL**: ORM or raw queries? Why?
- **Plain HTML/CSS**: Was this speed, honesty about my frontend skills, or both?
- **Anything else**: What else made the cut—and why?

---

## What I'd Do Differently

*The part that forces honesty—with myself and with readers.*

**Questions to answer:**
- What's already annoying me about this stack?
- What would I change in v2?
- What did I learn about *myself* as an engineer through this process?
- What question did I forget to ask at the beginning?

---

## Next Time

*Because the loop never really ends.*

**Questions to answer:**
- What problem am I excited to tackle next?
- What tool do I want to learn *just because*?
- How will I approach the next design differently?


## Problem Clarity
- What exact problem am I solving?
- Who experiences this problem the most?
- How are people solving this today?
- Why does the current solution suck?
- What would a "10x better" solution feel like?

## Scope Control
- What is the smallest version of this that still solves the problem?
- What can I remove without breaking the core value?
- What would a 1–2 day prototype look like?
- What feature am I adding only because it's familiar or easy?

## Reality Check
- If I had to ship this in 48 hours, what would it include?
- What part of this idea might users not care about?
- What assumption am I making that could be wrong?
- What would make someone use this twice?

## Learning / Comfort Zone
- What part of this requires me to learn something new?
- Am I avoiding something because it feels hard or unfamiliar?
- What technology or approach would I try if I wasn't optimizing for comfort?
- What would I build if I didn't care about doing it the "right" way?

## Build Bias
- What is the first thing I can build that proves the idea works?
- What is the ugliest possible version that still works?
- Can I fake part of this before fully automating it?
- What can I manually do behind the scenes at first?

## Iteration
- How will I know if this is useful within the first week?
- What signal would tell me to double down?
- What signal would tell me to kill it?
- What feedback would change the direction of the product?

## Personal Motivation
- Would I personally use this every week?
- Would I be excited to keep improving this for a month?
- Does solving this problem make my own life easier?





I asked Claude for stack ideas. It gave me several. I sat with them.

The document tracker clicked—not because it was the easy choice, but because it was the real one. This was my family's actual paperwork. Our actual move. Our actual stress.

I could have tried something exotic. A new language. A bleeding-edge stack. But coming off that interview, I'd spent a week deep in Python API practice. FastAPI was fresh in my fingers. Dictionary-based "databases" made sense. The muscle memory was there.

So I made a call: go deep, not wide.

Build the thing first. Learn the stack later. The problem mattered more than the tools.

So I built the entire backend with what I knew, the way I knew how.

**Was this the "right" choice?** Maybe. Maybe not. But it was the *honest* choice—and for a first version, that mattered more.

---

## What Familiarity Gave Me

- **Momentum**: I started building immediately instead of researching for two weeks
- **Confidence**: No imposter syndrome while learning a new stack mid-project
- **Depth**: Because the patterns were familiar, I could focus on doing them *better*

**Questions to answer:**
- What specific Python patterns did I dig deeper into?
- What did "greater capacity with deeper pythonic understanding" actually look like?
- What did I build that surprised even myself?

---

## What Familiarity Cost Me

- **Frontend struggle**: I knew Python, not CSS. That gap became the whole next chapter.
- **Possible dead ends**: Did I build something that won't scale? Won't be maintainable?
- **Growth velocity**: Did I learn a new stack's *surface* or deepen my primary stack's *core*?

**Questions to answer:**
- Where did my Python comfort zone hit its limit?
- What would have been easier with a different choice?
- Am I okay with those costs?

---

## The Deep Dive That Actually Happened

*Instead of going wide across technologies, I went deep into one.*

**Questions to answer:**
- What Python concepts did I finally *grok* through building this?
- How did my API design improve from v1 to v2 to v3?
- What did I reach for that I'd never used before? (type hints? pydantic? dependency injection?)
- Where did the code feel *beautiful* versus just *functional*?

---

## Where Familiarity Broke Down

*The front end.*

This is where Python couldn't save me. This is where I had to reach for something new—or someone.

**Questions to answer:**
- What happened when I tried to build the UI myself?
- Why did I ask Claude for a mockup instead of just pushing through?
- What did that moment teach me about my own strengths and blind spots?

---

## What I'd Do Differently

*Or would I?*

**Questions to answer:**
- If I started over today, would I pick Python again?
- What's the *one thing* I'd change about my approach?
- What did I learn about how I learn?

---

## Next Time

*Because the loop never really ends.*

**Questions to answer:**
- What stack *do* I want to learn next—and why?
- How will I balance depth vs. breadth going forward?
- What problem will force me out of my comfort zone?
