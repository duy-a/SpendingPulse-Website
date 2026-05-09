---
name: blog-post-generation
description: Generate reader-first, SEO-friendly Spending Pulse blog posts for this static website, including English and Vietnamese article pages, blog index updates, sitemap updates, topic tags, practical safe-to-spend guidance, and contextual app-positioned calls to action. Use for creating new app-related articles, topic ideas, tips, tricks, and practical safe-to-spend money guidance for Spending Pulse without turning posts into product-first feature tours.
---

# Blog Post Generation

Use this skill only inside the SpendingPulse-Website repo.

Goal: create complete, SEO-friendly Spending Pulse blog posts that are practical, app-related, and ready to publish in the static site.

## Editorial Positioning

Search intent comes first, but the article should not feel like a product pitch.

- Lead with the reader's problem, feeling, or decision moment.
- Use `hesitation -> clarity -> relief` as the default emotional arc.
- Treat "Feel good spending money again" as the emotional direction, not a slogan to repeat.
- Make the article useful even if the reader has not installed Spending Pulse.
- Do not turn articles into feature tours, update posts, demos, or release notes unless the user explicitly asks for that format.
- Let Spending Pulse appear as the natural tool near the end, after the article has already answered the reader's search intent.

## Required Sources

Before drafting, refresh app context from these external files when available:

- `/Users/duy_a/OneDrive/1. Projects/Spending Pulse - Marketing/Feature List.md`
- `/Users/duy_a/OneDrive/1. Projects/Spending Pulse - Marketing/App Store Description.md`

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

Make the visible article angle reader-first. For example, prefer "how to stop guessing before spending" over "Spending Pulse widgets." App surfaces are supporting proof, not the main subject.

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
- Add contextual internal links to other blog articles as references; never force privacy/terms links into unrelated articles.

## Article Images

Every new article must include one generated main image unless the user explicitly asks for text-only output.

Image requirements:

- Generate a related raster image for the article topic using the `imagegen` skill when available.
- Use one shared image for the English and Vietnamese versions of the same article.
- Save the image under `assets/blog/<slug>-hero.png`.
- Use a fixed `1200x630` image size, matching the Open Graph ratio.
- Do not include readable UI text, fake app screenshots, fake financial numbers, logos, or tiny chart labels inside generated images.
- Prefer realistic daily-money scenes, simple cash-flow planning objects, phone/watch context without legible private data, or clean editorial illustrations tied to the topic.
- Keep the image visually relevant to the specific article, not generic finance stock imagery.
- Write concise localized alt text for each language.

Article-page image placement:

- Add the main image immediately after `header.article-header` and before `article.article-content`.
- Use this pattern in English:
  - `<figure class="article-hero-image"><img src="../../assets/blog/<slug>-hero.png" width="1200" height="630" alt="..."></figure>`
- Use this pattern in Vietnamese:
  - `<figure class="article-hero-image"><img src="../../../assets/blog/<slug>-hero.png" width="1200" height="630" alt="..."></figure>`

Blog-index image placement:

- Add the same image as the first child inside the article card.
- English index pattern: `<div class="post-image"><img src="../assets/blog/<slug>-hero.png" width="1200" height="630" alt="..."></div>`
- Vietnamese index pattern: `<div class="post-image"><img src="../../assets/blog/<slug>-hero.png" width="1200" height="630" alt="..."></div>`
- All card images must use the existing `.post-image` wrapper so every image has the same ratio.

SEO image tags:

- Add absolute image meta tags to both language article pages:
  - `og:image`
  - `og:image:width` with `1200`
  - `og:image:height` with `630`
  - `twitter:card` with `summary_large_image`
  - `twitter:image`
- Use `https://spendingpulse.app/assets/blog/<slug>-hero.png` for all image meta tags.
- Add `og:title`, `og:description`, `og:type`, and `og:url` when creating a new article page so the image metadata has complete context.

## Article Structure

Create both language versions:

- `blog/<slug>/index.html`
- `vi/blog/<slug>/index.html`

Each article page must reuse the current site pattern:

- same navbar style and download icon
- correct relative paths for CSS/assets
- language switch linking English and Vietnamese versions
- article header with category, H1, lead, date, read time, and `Spending Pulse`
- generated main image after the article header
- article body inside `article.article-content`
- at least one contextual link inside `article.article-content` to another article in the same language
- avoid product mentions in the H1, lead, intro, and early H2s unless the article is explicitly product-focused or comparison-focused
- article body must stand alone as practical advice before any app bridge appears
- optional short `.article-cta` paragraph or short "where this fits" section explaining how Spending Pulse solves the problem, only when it fits naturally and late in the article
- bottom CTA section matching existing article pages
- same footer structure

Vietnamese copy must use proper Vietnamese diacritics.

## Internal Article References

Every article must include internal references to other blog articles:

- Add at least one link inside the article content, not only in the index, footer, language switch, or CTA.
- Prefer 1-3 links when they are natural and useful.
- Link to same-language article URLs:
  - English article pages should link to `../<other-slug>/`.
  - Vietnamese article pages should link to `../<other-slug>/`.
- Use descriptive anchor text that names the referenced idea, not generic text like `click here`.
- Keep links contextual: add them where the referenced article actually helps the reader.
- Do not link an article to itself.

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

- generated card image in the fixed `.post-image` ratio
- article link
- category kicker
- concise H3
- search-intent-aligned excerpt
- date and read time
- `.post-tags` topic chips that clarify what the article covers

Keep sidebar topics as the broad topic universe. Card tags should show the specific topics covered by that article.

Update the article count on each index.

## Sitemap

Update `sitemap.txt` with both URLs for every article slug, no exceptions:

- `https://spendingpulse.app/blog/<slug>/`
- `https://spendingpulse.app/vi/blog/<slug>/`

Keep existing URLs intact.

Before finishing, verify sitemap parity across all article folders:

- every `blog/<slug>/index.html` except `blog/index.html` has `https://spendingpulse.app/blog/<slug>/`
- every matching `vi/blog/<slug>/index.html` has `https://spendingpulse.app/vi/blog/<slug>/`
- every English article slug has a Vietnamese article folder
- every Vietnamese article slug has an English article folder
- do not treat the sitemap update as done if only the English URL exists

## Validation

After editing, run checks equivalent to:

- confirm both new article files exist
- confirm each new article has exactly one `<h1`
- confirm title and meta description exist
- confirm the generated image exists at `assets/blog/<slug>-hero.png`
- confirm the article hero image and blog index card image use the generated image
- confirm generated images are `1200x630` or keep the same `1200 / 630` ratio if the tool outputs a larger equivalent
- confirm `og:image` and `twitter:image` point to the absolute production image URL
- confirm blog index links point to the new slug
- confirm language switch links are correct both ways
- confirm each article body has at least one same-language link to another article
- confirm no article body links to itself as its only internal article reference
- confirm the article is not mostly about Spending Pulse features
- confirm the first half answers the search intent without requiring the app
- confirm product mentions are limited, contextual, and not repeated as filler
- confirm the emotional job is clear: less guessing, less overthinking, more calm spending confidence
- confirm sitemap includes both English and Vietnamese URLs for the new slug
- confirm sitemap includes both English and Vietnamese URLs for all existing article slugs, not only the new article
- `rg` for placeholders such as `TODO`, `TBD`, `Lorem`, and stale `featured` terminology
- `rg` likely unaccented Vietnamese phrases in `vi/blog`

If a local preview server is running, tell the user the exact article URLs to check.
