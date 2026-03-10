# Ether Blog — Setup & Usage Guide

## How it works

Drop a markdown file into `posts/`, add one line to `posts.json`, done.
No build step. No framework. No database.

---

## File structure

```
your-blog/
├── index.html         ← homepage (don't touch)
├── post.html          ← post reader (don't touch)
├── posts.json         ← your manifest (edit this)
└── posts/
    ├── my-first-post.md
    ├── another-post.md
    └── ...
```

---

## Adding a new post

### Step 1 — Write your markdown file

Create a file in `posts/` like `posts/my-new-post.md`.

Every file needs a frontmatter block at the top:

```markdown
---
title: Your Post Title Here
date: 2026-03-10
author: Your Name
category: Design
excerpt: A one-sentence summary shown on the homepage.
---

# Your Post Title Here

Your content starts here. Write normal markdown.

## A Subheading

Paragraphs, **bold**, *italic*, lists, blockquotes, code — all supported.

> A blockquote looks like this.

- List item one
- List item two

```code block```
```

### Step 2 — Add it to posts.json

Open `posts.json` and add an entry at the top of the array:

```json
[
  {
    "file": "my-new-post.md",
    "title": "Your Post Title Here",
    "date": "2026-03-10",
    "author": "Your Name",
    "category": "Design",
    "excerpt": "A one-sentence summary shown on the homepage."
  },
  ...existing posts...
]
```

That's it. The homepage will automatically show it.

---

## Deploying

### GitHub Pages
1. Create a GitHub repo
2. Push all files to the `main` branch
3. Go to Settings → Pages → Source: `main` branch, `/ (root)`
4. Your blog is live at `https://yourusername.github.io/repo-name/`

### Netlify (drag & drop — fastest)
1. Go to [netlify.com](https://netlify.com) and sign in
2. Drag your entire blog folder onto the deploy dropzone
3. Done — live in seconds with a free URL
4. For updates: drag the folder again, or connect your GitHub repo for auto-deploy

### Vercel
1. Push to GitHub
2. Import repo at [vercel.com](https://vercel.com)
3. No configuration needed — it's just static files

---

## Customizing

| What | Where |
|------|-------|
| Blog name | Search `Ether` in `index.html` and `post.html` |
| Accent color | Change `--accent: #c8a96e` in both files |
| Font | Change the Google Fonts link + font-family in CSS |
| Tagline | Edit the hero text in `index.html` |

---

## Categories

Categories are auto-detected from your posts — just use any string in the `category` field and it'll appear as a filter button on the homepage automatically.

---

## Tips

- Keep excerpts under 150 characters for best layout
- Date format must be `YYYY-MM-DD`
- Posts are sorted newest-first automatically
- The first post in `posts.json` is shown as the featured hero post
