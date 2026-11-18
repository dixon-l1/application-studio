# Changelog

Notable changes to Atrium Application Studio. Newest first.

## Unreleased

### Changed
- **Renamed to Atrium Application Studio**, from the Atria name used earlier the same day. Title, header, onboarding, backup filename, restore error and docs. The backup file's internal key is still `application-studio`, so every backup ever exported still restores. ([#10](https://github.com/dixon-l1/application-studio/pull/10))

### Added
- **Resume sections can be reordered.** Profile & data now has a Section order control: Professional Experience, Education and Skills, each with ↑ and ↓. Technical resumes usually lead with skills, and the order is one stored preference threaded through all three outputs — the live preview, the PDF layout and Copy as text — so they can never drift apart. An order that is missing, partial or unrecognised is repaired rather than trusted. ([#11](https://github.com/dixon-l1/application-studio/pull/11))
- **Memory across job descriptions.** Every match now records the posting's terms, the vertical it was written as, and the gaps Claude reported, in a `jdmemory` document private to each user and capped at the last 40 jobs. The Bullet bank tab shows which requirements keep coming up *and your bank cannot already answer* — anything your bullets already cover is filtered out — with a count of the postings each appeared in. "Draft bullets for these" asks Claude for draft bullets that fit roles you actually held, with every number left as a `[bracketed placeholder]` because only you know them. Nothing enters the bank until you accept it: each draft is editable, with its own role and skill, an Add to bank and a Discard, and a count on the Bullet bank nav link while any are waiting. ([#9](https://github.com/dixon-l1/application-studio/pull/9))
- **Suggested wording is now yours to accept or reject.** Claude's rewrites used to be applied silently, marked only with a "tailored" tag to undo. They now appear under the bullet they belong to, as a labelled suggestion with a ✓ and a ✕. Accepting applies it to this resume only; rejecting keeps your wording and is remembered, so re-running the match does not propose it again. Nothing touches the bullet bank either way, and the PDF always follows what you accepted. ([#8](https://github.com/dixon-l1/application-studio/pull/8))
- **Data Analytics vertical.** A fourth field guide with its own 12 skills (SQL and query craft, dbt modeling, self-serve BI, metric governance, experiment design, funnel and cohort analysis, forecasting, data quality, Python/R statistics, warehouse cost, stakeholder readouts, revenue and marketing analytics), bullet formulas, metric areas, seniority ladder, story types, rewrites, interview questions and prompt rules. Its rules make the decision the unit of achievement, treat a dashboard with no audience as a non-achievement, and treat a killed experiment as a legitimate result. ([#7](https://github.com/dixon-l1/application-studio/pull/7))
- **Per-job vertical targeting.** Each job is now written by one field's expert instead of a blend. A "Write this resume as" selector on the Tailor tab picks the vertical, defaulting to the one detected from the posting by scoring it against each field's own skill keywords. The match prompt opens as that field's expert resume writer, carries only that field's rules and skill list, and is told to keep the field's verbs rather than soften them into another field's wording. Quick match weights that field's skills too. ([#6](https://github.com/dixon-l1/application-studio/pull/6))

### Fixed
- **Software Engineering resumes read like Product Management resumes.** `matchPrompt` concatenated the rules for *every* field the user had selected and left the model to pick; the PM block led and its "outcome, not output" guidance stripped verbs like developed, debugged and implemented. The prompt now carries one field. ([#6](https://github.com/dixon-l1/application-studio/pull/6))
- **A product-management skill sat inside the engineering set.** "Product Feature Delivery" was skill 11 of 12 for Software Engineering, which is what tagged a SWE resume with product framing even once the prompt was isolated. Replaced with "APIs and Integrations". ([#7](https://github.com/dixon-l1/application-studio/pull/7))
- **Overlapping skill definitions sharpened** after an audit of all 48 skills: System Design vs Performance Optimization in engineering, Financial Modeling vs Forecasting and Business Case vs Strategic Planning in business operations, Growth vs Retention and Analytics vs Experimentation in product. Business Operations' "Data Analysis and SQL" became "Business Analysis and SQL" so it reads as decision support rather than competing with the new analytics vertical. No two skills share a name across the four fields. ([#7](https://github.com/dixon-l1/application-studio/pull/7))
- **The bullet bank's skill list was unreachable.** The left column now scrolls on its own instead of only moving with the bullet list, so the end of the skill list is reachable without scrolling the bullets to the bottom. ([#6](https://github.com/dixon-l1/application-studio/pull/6))

## 2026-11-17

### Added
- Renamed to **Atria Application Studio** across the title, header, onboarding, backup filename and restore error. The backup file's internal key stays `application-studio`, so backups exported before the rename still restore. ([#5](https://github.com/dixon-l1/application-studio/pull/5))
- New onboarding animation: two Romans carrying a bench, vases, plants and a statue into an atrium, replacing the stick-figure house build. Columns and architrave, a rippling impluvium, seven furnishings on a 7-second stagger, same reduced-motion fallback. ([#5](https://github.com/dixon-l1/application-studio/pull/5))

### Fixed
- A missing `profile` document no longer strands the rest of a user's saved work. `initDb` returned before reading the bank, roles and tracker, so an account holding real work but no profile document showed an empty app and onboarding. ([#4](https://github.com/dixon-l1/application-studio/pull/4))
- A single failed read no longer makes the whole session browser-only. The catch cleared the collection handle, so nothing else that session reached the account. ([#4](https://github.com/dixon-l1/application-studio/pull/4))

### Removed
- The "Jobs from chat" inbox, which was already switched off: `renderBulk` built its markup and then hid it, and `initDb` did not subscribe. Jobs reach the Bulk resumes tab by pasting a description into a slot. ([#3](https://github.com/dixon-l1/application-studio/pull/3))

### Security
- The chat inbox read from a top-level `inbox` collection. Only the `data/users/<uid>/` prefix is private per viewer, so on a shared copy one viewer's pasted job descriptions would have surfaced in every other viewer's Bulk tab. Scoped to `data/users/<uid>/inbox/items` before the feature was removed outright. ([#2](https://github.com/dixon-l1/application-studio/pull/2))
