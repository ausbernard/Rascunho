---
title: Partida - Live at Last
date: 2026-03-09
author: Berny
category: Design
excerpt: After all the planning, it finally runs. Here's what it looks like.
---

# Live at Last


For the past few posts, I've been talking *about* Partida. The idea. The philosophy. The stack.

Today, it actually runs. ✨

## Tracker

![Partida Tracker Dashboard](/posts/screenshots/partida-first-deploy.png)

**What you're looking at:**
- A family group with documents
- Color-coded statuses (red = not started, yellow = in progress, green = done)
- Document dependencies (some docs block others)
- A dashboard showing overall progress

It's pretty. It's not perfect. But it's *mine*, and it works on my machine.

### What Changed from the Prototype
The Python dicts are gone. 
```
## members
shared_family = ["primary", "spouse", "child1", "child2"]

personal_documents = {
    1: {
        "id": 1,
        "title": passport,
        "family_member_id": "primary",
        "depends_on": [],
        "status": "not_started"
    },
    2: {
        "id": 2,
        "title": passport,
        "family_member_id": "spouse",
        "depends_on": [],
        "status": "not_started"
    },
    # ... more docs
}

# Family Documents Dictionary (shared across all members)
"shared_documents" = {
    39: {
    "id": 39,
    "title": "Proof_of_Accommodation",
    "family_members": shared_family,
    "depends_on": [],
    "status": "not_started"  # One status for everyone
    },
    40: {
    "id": 40,
    "title": "Proof_of_Means_Subsistence",
    "family_members": shared_family,
    "depends_on": [],
    "status": "not_started"  # One status for everyone
    },
    # ... more docs
}
```
SQLAlchemy now handles persistence. FastAPI serves HTML directly, and HTMX swaps in updates. The Claude-generated frontend evolved as I connected real data.

![SQLAlchemy Schema](/posts/screenshots/partida-alchemy.png)

### What Breaks First

I ran it. `500 error`. 

The database tables were there. The schema was right. But the front end was failing because... there was no data.

I'd spent so much time modeling the structure—people, documents, statuses, dependencies—that I forgot the app expected data to exist. Tables without rows? Useless.

I needed to seed the database. In an in-memory configuration the data was already hardcoded and everything pulled from it.

So I wrote a quick script to populate:

- Our family members

- The 50+ documents we're tracking

- Initial statuses (all "not_started")

- Dependencies between documents

```python
# seed.py
# imports redacted

sys.path.insert(0, str(Path(__file__).resolve().parents[1]))

def seed_documents():
    """Seed the database with initial document data"""
    print("🌱 Seeding database...")
    
    # Create tables first (if they don't exist)
    init_db()
    
    db = SessionLocal()
    inspector = inspect(db.bind)
    tables = inspector.get_table_names()
    print("📊 Tables before:", tables)

    # Drop and recreate the problem table
    if 'learning_verbs' in tables:
        db.execute(text('DROP TABLE learning_verbs CASCADE'))
        db.commit()
        print("✅ Dropped learning_verbs table")

    # Let SQLAlchemy recreate it with correct schema
    models.Base.metadata.create_all(db.bind)
    print("✅ Recreated learning_verbs with correct schema")
    db.close()
    ...
    # script continues ...
```

Ran it. Refreshed the page.

It worked.

### Fixed It!
I ran it. I clicked around. I updated statuses. **Everything worked**.

Then I closed the terminal and reopened it. Data still there? **Yes. Good.**

Then I added modified a users name mid-session. Did the UI update? **Yes.**

Then I tried to break it on purpose.

**Found one:** when you add a new schema or table, you need to migrate your data. SQLAlchemy doesn't do that for you. I'd need to incorporate [Alembic](https://alembic.sqlalchemy.org/en/latest/) to handle schema changes without blowing away existing data.

## Verb Learner
My partner likes learning via flashcards. As we dive into learning Portuguese, she mentioned she wished she had a simple way to practice verbs. So I took our existing infrastructure—same database, same auth, same HTMX frontend—and added a page on top of it: **Learner**.

Pulled a nice json of 500 Portuguese verbs from [GitHub](https://github.com/jfoclpf/words-pt?tab=readme-ov-file), added a database table, wrote some API routes, passed those to the frontend and golden!

![Partida Verb Learner](/posts/screenshots/partida-verb-front.png)

A flashcard. A verb. Click the card.

![Partida Verb Learner Back](/posts/screenshots/partida-verb-back.png)

That's it. No complexity. No over-engineering. Just a small feature for one person that cost almost nothing to build because the foundation was already there.
This is the joy of building your own tools.

## What's Next
- Put it in front of my family
- Fix what confuses them
- Deploy somewhere real