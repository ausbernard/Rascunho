---
title: Partida - The Stack
date: 2026-03-07
author: Berny
category: Design
excerpt: HTMX, FastAPI, SQLAlchemy, actual technical decisions
---

# Partida - The Stack
## Where I Landed

### Architecture
I started with one database, one API, one server—all on localhost.

| Pros | Cons |
|------|------|
| Get a prototype out quickly | Scalability? What scalability? Can't put this in front of other families yet |
| Keep it simple | No idea how the database or server holds up under real load |
| Zero unnecessary overhead | Won't know what breaks until it breaks |
| Easy for my family to test on their own devices | |
---

### Database

#### In-Memory
I started with an in memory-database, Python Dictionary's. `personal_documents` and `shared_documents`. Nothing fancy.

I knew this wouldn't last. But for version one, it was enough to prove the logic worked. The next step was obvious, get a real database being it's one of our main components. 

And that's why I reached for a relational database - [AlchemySQL](https://www.sqlalchemy.org/).

#### AlchemySQL
SQLAlchemy is an open-source Python library that provides an SQL toolkit and an object–relational mapper for database interactions. In simple terms, it lets me stay in Python while talking to a database.

**Why it fits**
- relationship mapping made sense for my data, my data related to one other (people have documents, documents have statuses)
- could keep my object-oriented schema - stay within python
- data validation integrated naturally with my API
- no context-switching to raw SQL
- high reads, write are low
- schema is stable

It wasn't the sexiest or trendiest choice. But it was the right choice for where I was: a Python engineer who needed a database, not to detour into SQL mastery while prototyping.

---

### API 
Sticking with Python, the natural choice was between Flask and FastAPI for my API layer. Partida isn't a feature rich monster. If I ever needed some serious robustness I'd look at [Django REST Framework](https://www.django-rest-framework.org/). For now though? Lightweight is solid enough, we will see how it handles scale.

#### FastAPI
I considered [Flask](https://flask.palletsprojects.com/en/stable/). It's beautiful in its simplicity - I could have working API in under three minutes with 5 lines of code. 

But I kept coming back to data validation. Flask would mean piecing together packages: [Marshmallow](https://marshmallow.readthedocs.io/en/latest/) for serialization, something else for docs, and another thing for ... you get what I am saying.

[FastAPI](https://fastapi.tiangolo.com/) gives me a lot of things out of the box:
- **Pydantic** for data validation
- **Automatic OpenAPI docs** for free documentation I can leverage through my comments
- **Type Hints** which I am trying to use everywhere anyway

I knew I would end up here eventually. So I just started here instead.

---

### Front-End 
Realistically, my front-end skills lag far behind my visual aesthetic. I know what I want things to look like. Making them look that way? Different story.

I needed something clean, modern, and simple enough that my family could actually make sense of 50+ documents spread across multiple people. Individual progress. Group progress. Dependencies. Statuses. All in one place.

I drew sketches. They were... not good.

![Partida Sketch Bad](posts/screenshots/partida-sketch.JPG "Bad First Sketch")

I stared at it. Then I thought: I wonder how Claude would visualize this.

I like using AI to learn and ship faster. Sure, I could spend weeks brushing up on HTML, CSS, and the endless suffering of centering a div. Or I could ask for a starting point and iterate.

So I asked Claude:
> *Hey I'm building an application to track D7 visa documents for me and my family. It'll use FastAPI on the backend. I want to see how you'd design a front end for tracking documents with dependencies. Thinking color-coded statuses: 'notstarted' = pink/red, 'started' = yellow, 'finished' = green, 'blocked' = another color. Need pagination per user plus a total view. Here's my schema...*

It generated the first draft and well it was better than I imagined it was what I would agree is my standard but better than what I could imagine it was clean. It used HTML, CSS, and JS for web functionality and loading classes asynchronously as well as pulling from the API.

To link the front end to my api I leveraged HTMX to have my API just render HTML directly to the front end. This was sort of like magic and new out of my comfort zone. Still learning but it's been fun. I will make a blog on HTMX by itself to make sure I learn and understand why it does what it does but for my usecase it works!

It was better than anything I'd have built from scratch. Clean. Functional. Mine after I tweaked it.

---

### HTMX

Connecting it to the backend was where [HTMX](https://htmx.org/) came in. 

HTMX does one simple thing: it lets you make HTTP requests from any HTML element and swap the response into your page. That's it. No build step. No front-end framework. Just attributes like `hx-post` and `hx-swap`.

Instead of building a separate front-end framework (React), my API renders HTML directly. Magic? At first it felt like it. But really, it's just HTML being allowed to do what it does - hypertext. Hypertext just means text that links to other text—click a link, get a new page. HTMX extends that idea: click anything, get new HTML, swap it in place. Same concept, just more flexible.

Still learning. Still outside my comfort zone. But it works.

*I'll do a deeper dive on HTMX separately—it deserves its own post.*

## Next in the series

→ **[Partida - Reveal](/post.html?file=post/partida-reveal.md)**

