---
title: Partida - Taking Root
date: 2026-03-04
author: Berny
category: Open Source
excerpt: Denial is a great lesson, if you choose to allow it.
---

# Partida - Taking Root

Early in my first systems engineering role, a manager once told me, "You should always be applying, even if you love your job." And I do love my job—but like any good advice, it's worth listening to.

So when an interesting opportunity came along, I took the interview. I'd breezed through the coding rounds and landed on the part that makes every self-taught engineer's stomach drop: the System Design interview.

Here's the thing about being self-taught: you learn immensely on the job, but your expertise naturally orbits the systems you work with every day. You become a deep expert in your world. This role? It existed light-years outside that orbit.

I spent a week cramming—devouring everything I could about video and metadata processing systems.

I was **so** ready.

I **flopped**. Epicly.

From fumbling with the online whiteboard to struggling through basic data structure mock-ups. When it came time to discuss resiliency, scale, reliability... I didn't know where to start. The interview ended, and I felt—there's no other word for it—frustrated.

But here's the thing about good interviewers: they're also good humans. This one took a moment to tell me something I haven't stopped thinking about:


> I'd recommend building more things.
>
> Code. Deploy. Release.

> Solve your own problems, other people's problems, or business problems. I don't think grinding on our specific content pipeline problem is the best use of your energy.
>
> Instead, find a problem that's *yours*.
>
> Something in your world. A tool you've always wished existed. Or just something that bugs you day to day.

> Then run the full loop:
>
> **Figure out the problem → Design it → Build it → Ship it → See what breaks → Iterate.**
>
> That cycle, done on something you care about, compounds fast.
>
> And with AI coding tools now, you can move through it way quicker than even a year ago.


I didn't get that job. But I walked away with something better: a new direction.

## New Direction
It took me a while to figure out what to build. Then I thought about my family.

We've been increasingly interested in relocating abroad—except we had absolutely no idea where to start. So like any inquisitive human in 2026, I turned to LLMs to scope out the process.

Turns out, it's a lot. The sheer volume of documents required for one person is overwhelming. Add a spouse, maybe kids, and you're looking at three or four times the paperwork, the deadlines, the cross-referencing, the what-did-I-submit-and-to-whom chaos.

That's where *Partida* came in.

I turned to Claude with a simple prompt: `"Hey, I'm a software platform engineer... I need some ideas to solve problems of my own."`

It suggested a few directions—cost comparison tools, shipping optimizers—but one immediately clicked: a document tracker for visa paperwork. Apostilles, translations, expiration dates, renewal windows. The stuff that keeps you up at night when you're trying to move a family across an ocean.

**I started building**.

## Problem
Moving is messy. And despite all the political noise about "illegals," immigrating the "right way" takes an absurd amount of time, money, and organization. It's not cheap. It's not easy. And the paperwork? That's the whole job.

Take the Portugal D7 Visa. For one person, you need:

- Valid passport
- Two passport photos (EU standard)
- Signed visa application form
- FBI background check (apostilled)
- Proof of accommodation in Portugal
- Proof of sufficient funds (bank statements)
- Travel health insurance
- Flight itinerary
- Power of Attorney Forms
- NIF (Portuguese tax number) application
- Personal statement explaining reasons for move
- ...and the list keeps going

Now multiply that by a spouse. By kids.

Every document costs money. Every document has an expiration date. And every single one needs to be current and ready before you ever step foot in a consulate.

When you're in it, you're just drowning. You can work for weeks and feel no closer because there's no visual progress—just a pile of papers and a gnawing sense that you're forgetting something.

That's the problem I wanted to solve.

A dropdown to update a document's status. A graph showing 65% complete instead of just vague anxiety. Individual status. Family status. Something to remind you that you're actually moving forward, even when it doesn't feel like it.

## Partida
At its core, Partida is simple: a document tracker for people navigating the immigration maze. But I didn't want another spreadsheet-in-a-box. I wanted something that felt like the problem—organized but still messy, structured but flexible enough to handle the chaos of real life.

The first thing I built was the document tracker. Just a clean table showing what we had and what was missing. Basic CRUD stuff. Nothing fancy. I wish I'd taken pictures of that first prototype.

![First Design](/posts/screenshots/partida-first-diagram-design.png "first design ")


Coming off the interview, I'd been deep in Python API practice, so I stayed in that lane. I built an in-memory database with Python dictionaries. Functions for business logic. API routes to wire it all together. Tested every endpoint with cURL like it was 1999. Simple. Functional. Mine.

Once I had the core working—documents, metadata, ownership, dependency tracking, status reads and writes—I was ready for the front end.

Here's the thing: I'm picky about clean design, but I'm a backend engineer. Front-end is where my vision outruns my ability. So I asked Claude for help. Not to write the code at first—to imagine the interface.

Claude gave me a mockup.

I loved it.

![First Mockup](/posts/screenshots/partida-first-mockup.webp "first mockup ")

From there, the stack fell into place. I wanted something that felt like mine—not what I build at work, but what I want to build:

- **HTMX**- for dynamic updates (server returns HTML fragments instead of JSON)

- **Plain HTML and CSS**- for structure and style

- **Python FastAPI**- for the backend
  
- **Pydantic & Enum**- for data validation

- **AlchemySQL**- for the database because we needed the data to persist and something Python native

Nothing exotic. Just enough to move fast and solve the problem.


## Next in the series

→ **[Partida - First Principles](/post.html?file=partida-first-principles.md)**

→ **[Partida - The Stack](/post.html?file=partida-the-stack.md)**

Building Partida meant choosing tools that fit me—not what's popular, not what I use at work. Here's why I picked what I picked.
