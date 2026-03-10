# Rascunho Blog — Setup & Usage Guide

## Sketching systems in public
A blog about thinking through systems, one post at a time.

## Deployment
Currently deployed via **GitHub Pages**

## Post Requirements

| Field    | Format             | Required |
|----------|--------------------|----------|
| title    | Plain text         | Yes      |
| date     | `YYYY-MM-DD`       | Yes      |
| author   | Plain text         | Yes      |
| category | Plain text         | Yes      |
| excerpt  | ≤150 characters    | Yes      |

## How it works
- Posts are sorted newest first automatically
- The first post in posts.json becomes the featured hero on the homepage
- Categories generate filter buttons automatically—no manual configuration needed

## Categories

Categories are auto-detected from your posts — just use any string in the `category` field and it'll appear as a filter button on the homepage automatically.

---

## Tips

- Keep excerpts under 150 characters for best layout
- Date format must be `YYYY-MM-DD`
- Posts are sorted newest-first automatically
- The first post in `posts.json` is shown as the featured hero post
