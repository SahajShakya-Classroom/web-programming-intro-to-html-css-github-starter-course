# Copilot / AI Agent Instructions for this repository

Short: Static single-folder assignment (lab1) with standalone HTML pages (no build).

## Big picture
- This repo contains a small static portfolio site under `lab1/` (e.g., `index.html`, `home.html`, `about.html`, `projects.html`, `contact.html`, `navbar.html`, `portfolio.html`).
- No framework, tooling, or CI found. Changes are manual edits to HTML/CSS assets and previewed locally.

## Immediate workflows an agent should know 🔧
- There is no build step. To preview pages locally:
  - Open files directly in a browser (double-click) or
  - From the repo root run a lightweight server: `python -m http.server 8000` then visit `http://localhost:8000/lab1/` or use VS Code Live Server extension.
- There are no tests or linters present. Run an HTML validator or browser DevTools for quick checks.
- Use small, focused commits and PRs. Example PR title: `fix(html): correct paths in about.html` or `feat(css): add css/style.css`.

## Project-specific patterns & gotchas ⚠️
- Paths use Windows backslashes in several files (e.g., `images\avatar.png`, `css\style.css`). Prefer forward slashes in href/src attributes (e.g. `css/style.css`) to be platform-agnostic and valid URL paths.
- The site keeps a duplicated navigation block across pages (see `about.html` and `navbar.html`). There's no templating—update nav in every page when changing links/content.
- Several HTML files show structural HTML mistakes (misordered/mismatched `<head>` and `<body>` tags; nested `<nav>` tags). Examples:
  - In `about.html`, `<body>` starts before `</head>` and contains extra nested `<nav>` elements. Fixing structure improves renderer behavior and accessibility.
- Assets (CSS/images) appear referenced but may be missing from repo; create `css/` and `images/` if adding them.

## How to make safe, high-value edits ✅
- For fixes that change multiple pages (e.g., nav or path separators), prefer a single PR that updates all affected files and includes a short description of why the change is needed.
- When adding CSS, create `lab1/css/style.css` and update pages to use forward-slash paths (`<link rel="stylesheet" href="css/style.css">`).
- When adding or replacing images, place them in `lab1/images/` and reference them with forward slashes (`images/avatar.png`).

## Examples (what to change in place)
- Change backslashes to forward slashes:
  - Before: `<link rel="stylesheet" href="css\style.css">`
  - After:  `<link rel="stylesheet" href="css/style.css">`
- Fix head/body order in `about.html`: ensure `<head>...</head>` appears before `<body>...</body>`.

## Integration & CI notes
- No CI configuration detected. If you add linters/formatters or automated checks, add a small workflow under `.github/workflows/` and document it here.

## Pull request guidance for agents
- Keep PRs minimal and well-scoped.
- Use conventional-style titles (e.g., `fix:`, `feat:`) and explain why the change helps (cross-browser compatibility, accessibility, missing assets).

## Questions to ask humans (if uncertain)
- Where should assets (images/CSS) live—should they be added to `lab1/images` and `lab1/css`?
- Do you prefer to centralize the navbar with a templating approach or keep simple static pages?

---
If you want, I can open a follow-up PR to (a) normalize path separators, (b) add a minimal `css/style.css` placeholder, and (c) fix the invalid HTML files; tell me which you prefer and I'll proceed.