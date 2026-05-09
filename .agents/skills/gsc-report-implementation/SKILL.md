---
name: gsc-report-implementation
description: Analyze the latest Spending Pulse Google Search Console HTML report, classify recommendations, verify them against the current static website repo, and implement only still-valid repo-local website changes. Use when applying GSC report findings, SEO technical audit recommendations, sitemap/robots changes, metadata fixes, structured data fixes, or content recommendations from the website report folder.
---

# GSC Report Implementation

Use this skill only inside the SpendingPulse-Website repo.

Goal: turn the selected Google Search Console report into verified website changes without hardcoding any report-specific fixes.

## Report Source

Default report folder:

`~/OneDrive/1. Projects/Spending Pulse - Marketing/Marketing Efforts/Google Search Console/reports/`

Use the newest `gsc-*.html` report unless the user provides a specific report path or date. If no report is available, stop and say so.

## Before Editing

- Run `git status --short` and preserve unrelated dirty work.
- Before implementing any report recommendation, create or switch to a dedicated work branch so production stays untouched. Use `codex/gsc-report-YYYY-MM-DD` when the report date is known, otherwise use `codex/gsc-report-implementation`. If already on a non-production GSC work branch, confirm it before continuing.
- Never implement report fixes directly on the production branch. Treat `main`, `master`, `production`, and `prod` as protected branch names. If branch creation or switching fails because of dirty work, stop and report the blocker instead of editing production files.
- Inspect the selected report and the current repo before deciding what to change.
- Never trust checkbox state in the report. Report checkboxes are browser-only state; completion must be detected from files.
- Do not hardcode page counts, route lists, or expected fix types. Derive pages from actual `index.html` files plus sitemap/robots state.
- Do not implement external-only tasks such as submitting a sitemap in GSC. Report them as manual actions.

## Report Analysis

Extract recommendations from relevant sections, usually:

- Data Quality
- Canonical URL Setup
- Performance Snapshot
- Technical SEO Audit
- Sitemap & Robots
- Content Gaps
- Action Plan
- Open Questions

Classify every meaningful recommendation into one of four buckets:

- `implementable repo changes`: concrete changes to HTML, CSS, sitemap, robots, content, metadata, schema, or static assets in this repo.
- `manual external actions`: Search Console, Netlify, App Store, analytics, submission, or other work outside the repo.
- `analytics/watch-only findings`: observations, baseline metrics, wait-until dates, sparse data notes, ranking/CTR trends, or monitoring guidance.
- `not enough data / no action`: explicitly non-actionable findings or recommendations blocked by insufficient data.

Implement only `implementable repo changes` that are still missing or incorrect in the current repo.

## Implementation Rules

- Ground every change in report evidence and current repo inspection.
- Prefer structured HTML parsing or targeted metadata checks over broad blind replacement.
- Make changes idempotent: a second run must not duplicate tags, schema blocks, sitemap entries, or repeated content.
- Keep EN and VI routes paired when the report asks for language, canonical, hreflang, sitemap, or article work.
- Use the site's current URL, asset, layout, and copy patterns unless the report gives a concrete reason to change them.
- When a recommendation is already implemented, skip it and mention the proof.
- When a recommendation is ambiguous, implement only the unambiguous subset and report the ambiguity instead of inventing policy.

## Validation

Generate the validation checklist from the implemented recommendation types. Use only checks relevant to the current report.

Common checks include:

- metadata presence, uniqueness, and URL correctness
- sitemap/robots consistency
- canonical, hreflang, Open Graph, Twitter card, or schema validity when those were requested
- no duplicate tags or repeated JSON-LD blocks after repeated runs
- article/index/sitemap parity when blog content changes are involved
- same-language internal links when article changes are involved
- local HTTP checks for representative affected routes
- `rg` checks for placeholders such as `TODO`, `TBD`, `Lorem`, or stale report text

If a validation command cannot run, state the reason and what remains unverified.

## Final Response

Keep the final response short and include:

- selected report file
- implemented repo changes
- skipped recommendations with reasons
- validation performed
- any manual external actions still needed
