---
title: Partida - Lessons from The Prototype
date: 2026-03-07
author: Berny
category: Design
excerpt: This is what I built first before I knew better
---

# Ship fast and iterate. 

See what breaks. Leverage AI to help with debugging and sticky design points.

That was the plan. Here's what "version zero" actually looked like.

## Start Practical
I started with an in memory-database, Python Dictionary's. `personal_documents` and `shared_documents`. Nothing fancy
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

| Pros | Cons |
|------|------|
| Simple, visible data structure | It's localhost—when the server goes down, so does your data |
| Pure in-memory, no latency | No persistence means no real users |
| No SQL, no complex queries | Can't share data across sessions |
| Easy to track documents across members | Basically a prototype pretending to be a database |

---

I knew this wouldn't last. But for version one, it was enough to prove the logic worked. The next step was obvious, get a real database being it's one of our main components. 

And that's why I reached for a relational database - [AlchemySQL](https://www.sqlalchemy.org/). *But that's a story for another post.*

## Consistent Error Handling and Validation

## Data Validation is a Good Habit

## Separation > One Long Files