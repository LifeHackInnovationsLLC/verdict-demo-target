# verdict-demo-target

Throwaway **control target** for demoing **Ozura Verdict** (automated QA gate).

This is a trivial static web app (plain HTML + tiny inline JS, no framework). Vercel serves
it statically and builds a **preview deployment** on every push. The demo proves: push a
commit that introduces a bug → Verdict's GitHub status check turns **red** and **blocks** the
PR merge.

## Pages
- `/login` — email + password form; on submit, JS navigates to `/` (a successful "login" leaves `/login`).
- `/` — Landing page (`<h1>` + `<nav>` + `<main>`).
- `/settings` — `<h1>Settings</h1>`.
- `/profile` — `<h1>Profile</h1>`.

`vercel.json` sets `cleanUrls: true` so `/login`, `/settings`, `/profile` resolve to the
matching `.html` files.

## The bug toggle
The happy-path login check passes when `input[name="email"]` is present on `/login`.
**Removing that input** (the "bug") makes the check fail — which is what the demo pushes to
trigger a red status check.

## Notes
- Owned by **LifeHackInnovationsLLC** (LHI). Public, throwaway, **no real data, no secrets**.
- Connected to Vercel (team `ozura-inc`) for automatic preview deploys.
