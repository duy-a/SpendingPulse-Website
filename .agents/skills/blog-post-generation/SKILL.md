---
name: blog-post-generation
description: Generate SEO-friendly Spending Pulse blog posts for this static website, including English and Vietnamese article pages, blog index updates, sitemap updates, topic tags, and app-positioned calls to action. Use for creating new app-related articles, topic ideas, tips, tricks, and practical safe-to-spend money guidance for Spending Pulse.
---

# Blog Post Generation

Use this skill only inside the SpendingPulse-Website repo.

Goal: create complete, SEO-friendly Spending Pulse blog posts that are practical, app-related, and ready to publish in the static site.

## Required Sources

Before drafting, refresh app context from these external files when available:

- `/Users/duy_a/Desktop/Projects/SpendingPulse/SpendingPulse/docs/context/Feature List.md`
- `/Users/duy_a/Desktop/Projects/SpendingPulse/SpendingPulse/docs/marketing/App Store Description.md`

If either file is unavailable, continue from current website/blog copy and state that app feature context was not refreshed.

Also inspect current local patterns before editing:

- `blog/index.html`
- `vi/blog/index.html`
- an existing article page under `blog/`
- the matching Vietnamese article under `vi/blog/`
- `sitemap.txt`

## Topic Rules

Generate topics related to Spending Pulse and its actual app surface:

- safe-to-spend decisions
- daily money checks
- upcoming bills
- recurring income
- safety floors
- 30-day balance outlook
- widgets
- Apple Watch and complications
- reminders
- transaction tracking
- low-maintenance routines

Prefer concrete tips and tricks over generic finance advice.

Do not position Spending Pulse as a traditional budgeting, spreadsheet, accounting, or bank-linking app. The durable positioning is: a simple daily safe-to-spend signal based on recurring bills, income, balance, and safety floor.

## SEO Requirements

Every article must be SEO-friendly:

- Choose one primary keyword or search intent before drafting.
- Use a clean lowercase slug based on the topic.
- Keep the SEO title under roughly 60 characters where possible.
- Write a meta description around 140-160 characters.
- Use exactly one H1.
- Use descriptive H2 sections with natural search phrasing.
- Avoid duplicate title/meta descriptions across articles.
- Keep the blog index excerpt concise and aligned with search intent.
- Add internal links only when relevant; never force privacy/terms links into unrelated articles.

## Article Structure

Create both language versions:

- `blog/<slug>/index.html`
- `vi/blog/<slug>/index.html`

Each article page must reuse the current site pattern:

- same navbar style and download icon
- correct relative paths for CSS/assets
- language switch linking English and Vietnamese versions
- article header with category, H1, lead, date, read time, and `Spending Pulse`
- article body inside `article.article-content`
- optional short `.article-cta` paragraph explaining how Spending Pulse solves the problem, only when it fits naturally
- bottom CTA section matching existing article pages
- same footer structure

Vietnamese copy must use proper Vietnamese diacritics.

## Length and Read Time

Articles should be substantial enough to justify their displayed read time:

- Target 5-7 minutes depending on topic depth.
- Use roughly 900-1,300 English words for most articles.
- Vietnamese versions may have a different word count, but should feel equally complete and should usually be marked 5-7 phút đọc.
- Do not inflate read time for short posts. If the article is short, expand the article or lower the read time.
- Keep article-page read time and blog-index read time exactly aligned.
- Prefer adding practical examples, decision rules, setup checks, and common mistakes over filler.

## Blog Index Updates

Update both indexes:

- `blog/index.html`
- `vi/blog/index.html`

Add the new article to the article grid with:

- article link
- category kicker
- concise H3
- search-intent-aligned excerpt
- date and read time
- `.post-tags` topic chips that clarify what the article covers

Keep sidebar topics as the broad topic universe. Card tags should show the specific topics covered by that article.

Update the article count on each index.

## Sitemap

Update `sitemap.txt` with both URLs:

- `https://spendingpulse.app/blog/<slug>/`
- `https://spendingpulse.app/vi/blog/<slug>/`

Keep existing URLs intact.

## Validation

After editing, run checks equivalent to:

- confirm both new article files exist
- confirm each new article has exactly one `<h1`
- confirm title and meta description exist
- confirm blog index links point to the new slug
- confirm language switch links are correct both ways
- confirm sitemap includes both URLs
- `rg` for placeholders such as `TODO`, `TBD`, `Lorem`, and stale `featured` terminology
- `rg` likely unaccented Vietnamese phrases in `vi/blog`

If a local preview server is running, tell the user the exact article URLs to check.
