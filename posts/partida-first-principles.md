---
title: Partida - First Principles
date: 2026-03-02
author: Berny
category: Design
excerpt: "Building Partida meant choosing tools that fit me—not what's popular, not what I use at work. Here's why I picked what I picked."
---

# Design is Hard

I've learned something about myself: I make design choices based on *familiarity*.

The tools I've touched. What my current team uses. What feels safe.

Not research. Not deep technical understanding of why different technologies are actually present in architecture, at least not yet 😃

With Partida, I did it again. But this time I wanted a particular focus.

---

## The Honest Truth 

I had spent time learning and memorizing architectures without understanding the why. It was not until I read [I Thought I Knew System Design Until I Met a Google L7 Interviewer](https://medium.com/beyond-localhost/i-thought-i-knew-system-design-until-i-met-a-google-l7-interviewer-239385b24881) that I started to try and learn the why. 

The author describes freezing during a URL shortener design when asked: "What happens when you hit 10 million writes per second?" Not because they didn't know sharding or replication - but because they'd been "memorizing architectures without actually understanding why they existed in the first place."

This line hit me kinda hard.

Because that was me in my interview. I could talk about video processing pipelines. I had studied metadata systems. But when the conversation shifted from what to why—why this pattern over that one, why this trade-off, why this scale—I had nothing. I barely actually had the architecture memorized down. I had a shaky foundation.

The article goes on:

> "Senior engineers don't start with architecture diagrams. They start with numbers. Boring, unglamorous numbers. How many users? What's the read to write ratio? What's going to break first?"
>

That's the part I have been overlooking.

---

## What this means for Partida

Naturally, given my background—and my confessed habit of memorizing architectures I don't fully understand—I default to simple first. Build the thing, then add complexity when it's earned.

But while I was cramming for that interview, I caught myself doing something else entirely. I'd look at a problem and think: "Oh, I need a Redis cache here to show them I know caching. I need PostgreSQL for relational consistency. I need Kafka for—wait, do I actually need Kafka?"

I was designing for the interviewer, not for the problem.

For Partida, I wanted to be better.

Instead of reaching for patterns I've read about or asking an LLM for "WHAT I should use" I started with questions:

**What actually needs to be tracked?**

Documents and people. That's it. A person has documents. Documents have statuses. Everything else is decoration.

**How many users will use this application?**

At first? Just me and my spouse, running locally. But if it works—if it actually solves the problem—then eventually others. Some will self-host for their families. Others will want a hosted version where they can just log in and go.

That means designing for one user today, but not painting myself into a corner for tomorrow.

**Who needs to see what?**

Each person needs to see their own documents. Their status: not-started, in-progress, blocked, finished. And how those documents map across their family group—because a birth certificate isn't mine, it's ours, and its status affects everyone.

**What's the read-to-write ratio?**

Writes are rare. Status updates happen, but not constantly. Reads, though? I'd check every few seconds if the UI let me. That's overkill, but it tells me something: reads will dominate. Cache might matter someday. Just not yet.

**If this works, what breaks first?**

The database gets corrupted and I lose everything. Or I make a change, migrate the schema, and break existing data.

One is solvable with backups. The other requires thinking carefully about every change before I make it.

**Outside of the base design, what features can be added?**
- Document expiration (adding fields to our database: `created_at`, `last_updated`)


This is uncomfortable. It's slower. It forces me to admit what I don't know. But that's exactly the point.

---

## Next in the series
I landed on HTMX, FastAPI, and AlchemySQL. Check out the next series for the thoughts.


→ **[Partida - The Stack](/post.html?file=partida-the-stack.md)**