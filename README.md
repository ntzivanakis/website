# nikostzivanakis.com

Personal academic website of Nikolaos (Nikos) Tzivanakis, built with [Hugo](https://gohugo.io/) and hosted on GitHub Pages behind Cloudflare.

Every push to `main` rebuilds and deploys the site automatically (about 30 seconds). You can edit any file directly on GitHub: open it, click the pencil icon, make the change, and commit.

## Where things live

| To change… | Edit |
|---|---|
| A paper, report, or working paper | `data/research.json` |
| A blog post | `content/blog/` (one file per post) |
| Data sources page | `content/data.md` |
| CV | `content/cv.md` |
| Consulting page | `content/consulting.md` |
| Contact page text | `content/contact.md` |
| Profile links (Scholar, ORCID, SSRN, LinkedIn) | `hugo.toml` → `[[params.profiles]]` |
| Homepage bio and title | `layouts/index.html` |
| Menu | `hugo.toml` → `[menu]` |
| Colours and styling | `static/css/style.css` |

## Adding a paper

Add an entry to `data/research.json`. It appears on the Research page and, if it is among the three most recent, on the homepage too.

```json
{
  "type": "journal",
  "date": "2026-09-01",
  "title": "Paper title",
  "url": "https://doi.org/...",
  "venue": "Journal Name, 2026",
  "desc": "One or two sentences. With Co-author & Co-author."
}
```

- `type` is one of `journal`, `working_paper`, `report`, `bulletin`, `thesis`.
- `date` controls ordering (newest first) and the year shown for working papers.
- `venue` is optional; working papers don't use it.
- `extras` is optional HTML shown under the description (e.g. software links).
- Mind the commas between entries — JSON is strict. If the deploy fails, check the Actions tab.

## Adding a blog post

Create a file in `content/blog/` named `YYYY-MM-DD-short-title.md`:

```markdown
---
title: "Post title"
date: 2026-09-01
---

Write the post here in Markdown. **Bold**, *italic*, [links](https://example.com).

## A subheading

More text.
```

It appears on the Blog page and, if it is the newest post, on the homepage. Add `draft: true` under the date to hide a post without deleting it.

## Previewing locally (optional)

```bash
hugo server
```

Then open http://localhost:1313.
