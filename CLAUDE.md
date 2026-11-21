# Atrium Application Studio: notes for Claude

## What this is
A single-page app (`index.html`, plain HTML/CSS/JS, no build step) that tailors resumes, cover letters and application answers to each job from one bank of accomplishment bullets. It's a public portfolio project. The owner is a product manager who shows it to recruiters.

## Hard rule: no personal data in this repo
The repo is public. Never commit a real person's resume content, phone, email, address, employer details or bullets. Screenshots and examples must use made-up profiles (the current ones use "Jamie Rivera"). The screenshots are generated, not hand-taken: a seed script builds that fictional profile into a throwaway copy of `index.html` and headless Chrome captures it (`--headless=new --virtual-time-budget=... --window-size=W,H --screenshot=out.png`, 1440x1100 for the full views, card-sized windows for the two overlay shots, and a negative `animation-delay` on `.scene .it` to hold the atrium mid-cycle). Regenerate them the same way rather than screenshotting a real account. The owner keeps a personal copy of the app with his own data on claude.ai. That copy never goes in this repo. Commit with the GitHub no-reply email, not a personal one.

## How it runs
- It's built to run as a Claude artifact on claude.ai. The runtime gives `window.claude.use(name)`, which returns capability objects:
  - `sample(prompt, {modelTier, signal, onText})` and `sample.json(...)` for Claude calls. These can't browse the web.
  - `db` for per-user storage under `data/users/<uid>/<key>`.
  - `user.id()`.
  - `downloads.save({filename, data})`.
- Each person who opens the shared artifact runs on their own Claude plan.
- Viewers with view-only access can't write `db`, so the app falls back to `localStorage` (keys prefixed `as1.`). There's also a JSON backup and restore under Profile & data.
- Opened as a plain file, Claude features are unavailable. Quick match, PDFs, the tracker and manual setup still work.
- Libraries load from cdnjs: jsPDF 2.5.1, JSZip 3.10.1, mammoth 1.6.0 and pdf.js 3.11.174 (its worker is loaded via a script tag). The page can't reach other hosts, so job links can't be fetched. Users paste the job description.

## Structure inside index.html
- **Data layer:** `PROFILE`, `ROLES`, `FIELDS`, `SETTINGS`, `STORIES` and `FIELD_SPECS`.
  - `FIELD_SPECS` is the field guides for pm, swe, bizops and data, inlined from `research/field-guides.json`. Each job is written by one vertical only: `detectField()` scores the posting against each field's keywords and `activeField()` prefers the user's pick from the Tailor tab, then the prompt carries that field's rules and skills alone.
  - Each vertical also carries an `expert`: a named person the prompts write as (PM: CPO of Notion; SWE: staff engineer at Meta; bizops: COO of Meta; data: lead data engineer at Meta). `fieldExpert()` reads it and `reviewRules(who)` is the final self-review pass appended to every prompt that produces a bullet - tailoring, gap drafting, notes and document import, and the onboarding bank build. Adding a prompt that writes bullets means appending `reviewRules` to it too.
  - `rebuildSkills()`, `fieldRulesText()`, `skillNames()`, `buildQuestions()` and `defaultPicks()` derive the rest.
- **Persistence:** `persist(key, data)` writes `localStorage` first, then the db. `initDb()` and `loadLocal()` load it back.
  - Keys: profile, roles, bank, answers, resumes, letters, letterstyle, tracker, bankmeta, jdmemory, edits.
  - `edits` is this person's own rewrite history: up to 60 `{at, id, role, skill, before, after}` pairs, written by `recordEdit` whenever a bank bullet is saved with changed text. `editTendencies()` measures them and `editStyleText()` turns them into the prompt block that every bullet-writing prompt carries, ahead of `reviewRules`. Rebuild it, never mutate it. A bullet saved by hand also goes to `reviewEdit()`, which asks that bullet's own vertical's expert for a keep-or-improve verdict shown under the bullet; it must never apply a rewrite on its own, and it drops one that would lose a `[placeholder]`.
  - The storage runtime freezes what it is handed, so `persist` sends a copy and `initDb` copies what it reads (`thaw`). Everything here is edited in place somewhere, so never pass live state to `col.doc().set()` or assign a document straight to a module variable.
  - `jdmemory` holds the last 40 matched postings' terms and gaps plus bullet proposals awaiting sign-off. Rebuild it rather than mutating it, and never let recording a job fail a match.
- **Views** (hash routes): tailor, bulk, letter, bank, answers, tracker, guide. The tailor tab is called **Single resume** in the interface; the route and the function names stay `tailor`.
- **Colour:** the accent is `#906D97`, a muted purple. `--accent`, `--accent-soft`, `--accent-ink` and `--hover`, defined three times (light, the dark media query, the dark attribute). `--accent` is the colour itself and belongs on plates, borders and fills; anything that is accent-coloured *text* on a light background uses `--accent-ink`, the darker shade of the same hue, because the accent alone does not carry body text. The greys around it are neutral with only a trace of violet; do not tint them toward the accent. The `.paper` rules use literal colours on purpose, because the page stays light in either theme - change both. `PALETTE` is the 18-hue wheel that colour-codes skills; it is data coding, not the interface, and is deliberately not sage.
- **Onboarding overlay** (`#ob`), four steps:
  1. Pick fields.
  2. Upload resume, bullet bank and writing samples.
  3. Line-art animation of two Romans carrying benches, statues, vases and plants into an atrium while three Claude calls run: parse the resume, build the bank, and learn the writing style.
  4. The app opens.
- **Profile and data modal** (`#pf`): edit education, sections and fields; backup, restore, start over.
- **Bulk runs use Claude for every job**, falling back to `computeQuick` only when the capability is missing or refused; a job that fell back sets `j.quick` and says so on its card. The run button's label follows the same fact, so it never promises Claude when Claude is not there.
- **Bullet rules everywhere:** never invent numbers, put a missing number in a `[bracket placeholder]` with a fallback version of the bullet, no em dashes, one skill per bullet.

## Testing
Run headless Chrome with Playwright. Mock `window.claude` with an init script that returns canned JSON for each prompt; match on the prompt's first words, e.g. "Extract structured data", "You are an expert resume writer", "You are tailoring", "Write a cover letter". For offline tests, swap the cdnjs URLs for local copies of the libraries. Check `pageerror` events and take screenshots of each view.

## Decisions already made
- **Vercel or another standalone host:** this would need a server-side Claude API key, billed separately through the Claude Console. Anthropic doesn't allow third-party sites to sign people in with a Claude plan. The owner chose to keep it on claude.ai so each friend uses their own plan.
- **Research:** `research/notes.md` is the raw research. `research/field-guides.json` is the reviewed spec of formulas, skills, metrics, rewrites, seniority signals and questions for each field.
