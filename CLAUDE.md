# Project

Multi-page static site on Cloudflare Pages. Single domain, path-based routing.

## Rule of the repo

- **One folder = one page = one URL slug.** Folder `example/` serves at `/example/`.
- All pages are plain HTML/CSS/JS. No build step. No framework.
- To create a new page, copy `_template/` — or run `/new-page <slug>`.

## Naming

- Slugs are kebab-case: `sales-black-friday`, not `salesBlackFriday`.
- The slug is the URL. Don't rename folders after launch (breaks links).

## Where things live

- `_template/` — scaffold for new pages. Don't edit except to improve the template.
- `shared/` — CSS/JS/fonts used by 2+ pages. Create only when real duplication appears.
- `_headers` — cache rules. `/shared/*` cached for a year; HTML is not cached.
- `.claude/commands/` — slash commands (e.g. `/new-page`).
- `docs/` — architecture and onboarding docs (shareable).

## Performance defaults (keep these)

- Inline critical CSS in `<head>`.
- `<script>` tags are `defer` or `async`. Never blocking.
- Images: `loading="lazy"`, `decoding="async"`, WebP/AVIF when possible.
- Use `<link rel="preload">` for the hero image and the above-the-fold font.
- `<link rel="preconnect">` to any third-party origin (pixels, analytics) before loading its script.

## Do not

- Duplicate trackers across pages — when trackers arrive, they live in `shared/scripts/`.
- Add a bundler, package.json, or framework without asking.
- Put secrets in client-side code.
- Rename a launched folder without a matching `_redirects` entry.

## Deploy

Cloudflare Pages, single project pointing at repo root. Push to the connected branch.
