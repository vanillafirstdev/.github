# VanillaFirst

**Reach for the platform first.** Plain HTML, CSS, JavaScript, PHP and SQLite. No `npm install`, no `composer install`, no build step, no framework.

Three starter kits build the same app, a bookmark list, so you can see exactly what each layer adds:

| Kit | What it is | Where the bookmarks live | Run it with |
|---|---|---|---|
| **[Frontend Kit](https://github.com/vanillafirstdev/frontend)** | HTML pages, CSS, ES modules and a Web Component. No server code. | `localStorage`, seeded from a JSON file | Any local web server: `python -m http.server 8000` |
| **[Backend Kit](https://github.com/vanillafirstdev/backend)** | A JSON API in PHP. No pages. | SQLite, behind `/api/bookmarks` | `php -S localhost:8000 -t public`, then `requests.http` |
| **[Full-Stack Kit](https://github.com/vanillafirstdev/fullstack)** | The same list twice: rendered on the server with a form, and rendered in the browser from its own JSON API. | SQLite, behind pages and `/api/bookmarks` | `php -S localhost:8000 -t public` |

Each kit is a template repository: click **Use this template** to start your own copy with a clean history.

## Which one?

Ask two questions: **does anything need saving on a server?** and **will anyone sign in?**

- Nothing saved on a server → **Frontend Kit**.
- Data saved, but this project serves no pages → **Backend Kit**.
- Data saved, pages served, nobody signs in → **Full-Stack Kit**.
- People sign in → **[VanillaSaaS Core](https://vanillasaas.dev)**, free under the MIT licence: hashed passwords, expiring reset tokens, sign-in rate limiting and session timeouts, already written.

Don't bolt a login onto a kit. Starting on a kit because it looks simpler, then adding accounts in month two, means hand-writing the code most likely to leak your users' data. Each kit's README has the full decision table, including when to run a kit and Core as two separate sites.

## What the kits share

- **Conventions:** `public/` as the only web root, relative links so everything works in a subfolder, a Content-Security-Policy that blocks inline JavaScript and CSS, `textContent` instead of `innerHTML`, `http(s)`-only stored addresses, and SQLite in WAL mode with a busy timeout.
- **Files:** the Frontend and Full-Stack Kits share their CSS, form validation and Web Component byte for byte; the Backend and Full-Stack Kits share their router, validation rules and API controller. Moving between kits means swapping one module, not rewriting the app.
- **AI instructions:** every kit ships an `AGENTS.md` that tells Copilot, Cursor, Codex and Claude Code the codebase's rules and how to review against them.
- **Limits, stated plainly:** no accounts in any kit, one writer at a time and one server for SQLite, and PHP versions that change under you if you don't pin them.

## For teaching

The kits follow a frontend, backend and full-stack sequence. A frontend unit covers semantic HTML, CSS tokens, Grid and container queries, modules, form validation, `fetch()`, Web Components and `localStorage`. A backend unit covers HTTP methods and status codes, one error shape, validation, prepared statements, CORS and API keys, tested without writing a client. A full-stack unit covers sessions, CSRF tokens, Post/Redirect/Get and security headers, then the frontend code calling the backend API on the same page.

As template repositories, the kits work as starter code for GitHub Classroom assignments. When a brief requires students to build a login themselves, VanillaSaaS Core's commented `auth.php`, `session.php`, `password_reset.php` and `throttle.php` are the reference to read first.

---

MIT licensed. Maintained by Len Johnson, who posts about VanillaFirst as @lenjohnson.uk on [LinkedIn](https://www.linkedin.com/in/lenjay), [TikTok](https://www.tiktok.com/@lenjohnson.uk) and [Instagram](https://www.instagram.com/lenjohnson.uk).
