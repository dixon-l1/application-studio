# Resume research notes: PM, Software Engineering, Business Operations

Compiled from web research (Nov 2026). Paraphrased; source URLs listed per section. Use as input to define per-field bullet and language structures.

---

## 1. Product Management (from earlier research for this project)

**What reviewers scan for**
- Outcome-first bullets: lead with the result, method in a "by doing" clause (Google XYZ: "Accomplished X as measured by Y by doing Z", Laszlo Bock).
- Name the decision the PM made (prioritized, cut, killed, tested, sequenced) so the PM's part is separable from the team's.
- Every metric gets a baseline + timeframe ("from 2.1% to 2.8% in one quarter"), not a bare "+30%".
- Scope signals level: users reached, revenue, teams aligned, budget.
- One consistent positioning; strongest bullet first in each role; 3-4 bullets current role, fewer for older roles.
- User research / discovery bullet now nearly expected (Netflix/Rippling/EvenUp hiring-manager panel, Lenny's Newsletter x The Skip).
- AI fluency questions common in PM loops (Sierra, DoorDash, Datadog, Perplexity).

**PM metrics**: adoption/engagement (DAU/WAU/MAU, feature uptake), revenue/conversion (ARR, conversion, ACV), retention (churn, NRR), efficiency (hours saved, tickets deflected), speed (time-to-market, % of roadmap shipped), discovery (interviews, prototype tests, experiments), customer experience (onboarding time, NPS/CSAT), scale (users, markets), leadership (teams aligned).

**PM story types**: 0-to-1 launch ("first X"), metric-moving optimization, data-led insight, discovery-driven bet, kill/cut decision, cross-team alignment at scale, infrastructure framed as business value, expansion (more than the team thought possible), enterprise/customer win, process change that outlasted you.

**Company emphasis**: Meta = impact + speed; Google = scale/systems + XYZ; Amazon = ownership + data mapped to Leadership Principles; Netflix = judgment without supervision; Apple = craft and depth; Stripe = rigor, writing, owning outcomes (application asks proudest launch + biggest mistake); Atlassian = values (customer, teamwork); startups = specific shipped work, stage fit.

**Avoid**: "Responsible for", "Worked with", "Helped", "Managed the roadmap" with no result, rituals as achievements (standups, sprint planning), tool lists inside bullets.

Sources: igotanoffer.com/blogs/product-manager/product-manager-resume; enhancv.com/resume-examples/faang; novoresume.com/resources/resume-examples/product-manager; site.joinleland.com (PM resume guide); underdog.io/blog/product-manager-resume-template; teamblind.com (startup PM to Meta L6); the-pm-archive.vercel.app (Lenny's x The Skip hiring managers); stripe.com/jobs/product-manager-jd.pdf; inc.com + businessinsider (Bock XYZ formula).

---

## 2. Software Engineering

**Bullet formulas found**
- Tech Interview Handbook (techinterviewhandbook.org/resume): "[Accomplishment summary]: [Action] that resulted in [quantifiable outcome]"; begin each role with scope + skills, then top accomplishments; a few best achievements beat many average ones; mirror JD keywords naturally (no stuffing); write out abbreviations once; skills line grouped by languages / frameworks / databases; one page; reverse chronological; Education first if <3 years experience.
- Gergely Orosz (ex-Uber EM; The Tech Resume Inside Out; freecodecamp article): ~6-second scan; screeners check fit against the JD first; master resume then cut; reorder bullets/skills to match posting; focus on what you achieved; XYZ-style structure; active verbs (led, drove, improved, rolled out); **put technologies toward the end of a bullet** — impact first, tools help detailed readers; quantify (team size, code coverage before/after, SLA changes, revenue, users, installs, ratings, tickets); example: "widely adopted" -> "3-person team built a framework adopted by 15 teams and 50+ developers"; give links context.
- Ex-Amazon SDE (codingshuttle): [Action verb] + [What you built] + [Tech stack] + [Measurable result].
- devplaybook: [Action verb] [what you built/changed] [by doing X] [resulting in Y]; 3-5 bullets/role, 1-2 lines; avoid Helped/Assisted; approximations OK (~40%) but only defensible numbers—interviewers ask about every number; one page under ~8 years.
- techinterview.org (quantifying impact): action + scope + outcome; strong verb, scale, measured result.

**Metric categories by sub-discipline (techinterview.org)**
- Backend/infra: throughput (QPS, events/day), latency percentiles (p50/p99), reliability/error rates, cost per request, scale.
- Frontend/mobile: user-facing performance (LCP, load time, bundle size), conversion/engagement, crash rate, A/B results.
- ML/data: accuracy vs baseline, training/inference time, pipeline throughput, cost per inference, business impact.
- DevOps/SRE: incident frequency, MTTR, deploy frequency, lead time, cost savings, tool adoption, SLO attainment.
- Eng management: team growth/retention, hiring outcomes, cross-functional impact, team-level metrics.
- Without exact numbers: approximate scale anchored to what you can defend, relative deltas, side-by-side comparisons (replaced X with Y), effort signals (team size, # services, PRs).
- Team vs individual credit: tie outcome to your specific work; don't claim leadership of work you only contributed to ("contributed substantial portions of" is still strong).
- Avoid: vanity metrics (lines of code), vague intensifiers ("significantly improved"), duty lists.

**Example bullet patterns (paraphrased from devplaybook)**
- Backend perf: added caching + query indexing, response time 400ms -> 45ms at 2M daily requests; moved sync payments to a queue, tripling checkout throughput; connection pooling cut DB CPU 35% at peak; S3 transfer costs -40% via CDN caching.
- Reliability: automated failover, DB downtime ~4h/month -> <2 min; tracing across 12 services cut time-to-identify issues 45 -> <10 min; circuit breaker kept checkout at 99.7% availability during provider outages; migration to managed containers saved $85K/yr and raised deploy success 94% -> 99.6%.
- Frontend: initial load -52% via code splitting/SSR; bundle 4.2MB -> 1.1MB; LCP 4.8s -> 1.9s; form abandonment -23%; WCAG 2.1 AA compliance; build tool migration cut dev startup 45s -> 3s; component library cut feature UI time 35%.
- Testing: E2E tests on 45 critical flows catching ~3 regressions/release.
- Full-stack: collaboration feature used by 30K users in month one; billing system reaching $120K MRR in 6 months; legacy rewrite cut load time 65% and tripled deploy frequency; polling -> WebSockets at 10K events/s; search 3.2s -> 150ms over 50M records.
- Infra/DevOps: K8s cost -$45K/yr; GitOps rollback <90s; secrets moved to vault across 28 services for SOC 2; DR with 15-min RPO / 1-hr RTO.
- Leadership: led 6-engineer team delivering platform on schedule; on-call + runbooks cut MTTR 2.5h -> 35 min; mentored 3 juniors, all promoted within 18 months; bi-weekly releases -> continuous deployment (14 days -> 2 hours merge-to-prod); design doc template adopted by 4 teams.

**Seniority (techinterview.org, novoresume, resumegeni, greatfrontend)**
- New grad: internships/projects, defensible metrics, Education near top.
- Mid: ownership + concrete outcomes.
- Senior: scope, judgment, risk reduction, technical direction, influence through others; "the senior resume is not a longer mid-level resume" — shift from implementation output to ownership quality (owned a flow/migration/system/quality bar). Test: could a staff engineer ask about this line for 10 minutes? Current role 3-4 bullets.
- Staff+: strategic direction, mentorship at scale, external influence, design docs/RFCs that changed roadmaps of teams you don't manage; scope = problem domain, not headcount. Don't over-claim staff scope at senior ("set technical strategy for the entire org").

**FAANG / company emphasis**: Meta leads with product impact + speed shipped; scale of work and what it changed (novoresume FAANG); Google XYZ.

**Skills section**: languages | frameworks | databases | cloud/infra | tools; list technologies on first page (Orosz).

Sources: techinterviewhandbook.org/resume; freecodecamp.org/news/how-to-write-a-developer-resume-recruiters-will-read (Orosz); techinterview.org quantifying-impact-engineering-resume; techinterview.org senior-engineer-resume and staff-principal-engineer-resume; devplaybook.cc/blog/software-engineer-resume-50-bullet-points-star-format; codingshuttle.com (ex-Amazon SDE guide); novoresume.com senior-software-engineer; greatfrontend.com/blog/senior-frontend-developer-resume; resumegeni.com backend-engineer/staff; igotanoffer.com/blogs/tech/software-engineer-resume-examples; enhancv.com/resume-examples/faang.

---

## 3. Business Operations / Strategy & Operations (BizOps, S&O)

**Who gets hired**: most S&O hires come from consulting (McKinsey/BCG/Bain/Deloitte etc.), then investment banking, PE, corporate strategy, finance (rocketblocks career-path & breaking-in). Postings often require 2+ yrs top consulting/IB/PE or 4+ yrs BizOps at high-growth tech. Google BizOps resume screen looks for analytical rigor, leadership, impact via consulting/strategy/cross-functional roles (Leland). Non-consultants should translate their work into recognizable strategy/ops vocabulary.

**BizOps sub-functions** (igotanoffer): Product BizOps, GTM BizOps, Sales Ops, Strategy & Insights, Customer Success BizOps, Finance BizOps, Data & Analytics BizOps.

**Hard skills to show concretely** (RocketBlocks, LinkedIn S&O): financial modeling, business case building, querying (SQL), data visualization/dashboards. Be specific: not "created dashboards for leadership" but which dashboards, for what decision, with a % performance improvement. Bridge missing skills with certificates or adjacent tools.

**Soft skills shown via bullets** (RocketBlocks examples, paraphrased): communication (prepared company-wide financial plan communications from CEO to field), influence (drove C-suite alignment on 3-year strategy tied to measured growth), decision-making (selected core CRM vendor from business case through contract with expected ROI), teamwork (led cross-functional team implementing new processes across teams with measured gain). Group grey-area skills (strategy, ops, PM, insights) visibly.

**S&O "scrappiness"** (DoorDash S&O author, howtosurvive substack): analytical thinking (data -> actionable recommendation), communication & influence without authority, scrappiness (initiative, creative problem solving, limited resources). Tactics: quantify every bullet with BOTH input metrics (scale/effort: people served, # markets, # stakeholders) and output metrics (revenue, growth %); show both strategic AND operational work (plan and execute); highlight process creation/improvement. Experience inventory: master list of every project with skills + results, tailor per job.

**What hiring managers want** (Leland BizOps guide): quantified before/after, scale, time saved (estimates OK if explainable); cross-functional collaboration (finance, supply chain, marketing, product); process optimization (workflows, automation, throughput); data-driven decisions (dashboards, KPIs, financial analysis); at manager level, long-term planning not just daily ops; certifications sometimes (PMP, Lean Six Sigma).

**Metrics emphasized**: cost savings / opex reduction ($ annualized), revenue impact / growth, ROI, cycle time and throughput, efficiency %, automation rate (manual -> automated), hours saved, forecast accuracy, on-time delivery/resolution time, SLA, headcount/capacity planning accuracy, unit economics (CAC, LTV, margin), pipeline / bookings for GTM ops, team size, # markets launched.
- Example patterns (paraphrased, Leland): analyst identified ~$500K annual savings via staffing/logistics modeling; cut manual reporting consolidation 70% with SQL + Excel models; manager oversaw $60M division with 120-person team, cut ~$800K annual opex, automated ~40% of manual tasks.
- Operations analyst impact chain (resumegeni): Analysis performed -> Insight generated -> Business outcome. Avoid listing tools without the decision they drove.

**Mistakes**: duty statements ("responsible for operations"), no metrics, not tailoring, omitting process/cost/data work, dense text (4-5 second scan), first-person pronouns.

**Structure**: short results-focused summary (no objective); key skills matching posting; reverse-chronological, 3-5 results-focused bullets per role (more for current, 2-3 for older); education + relevant certifications; 1-2 pages; ATS-safe.

**Narrative**: resume shows what you did; interview explains why (RocketBlocks). Interviews are case-heavy; resume bullets should read like mini-cases (problem -> analysis -> recommendation -> result).

Sources: rocketblocks.me/blog/bizops-resume-tips.php; rocketblocks.me/guide/bizops/career-path.php; rocketblocks.me/guide/bizops/breaking-in.php; howtosurvive.substack.com/p/so-how-does-one-pass-the-resume-screening; joinleland.com/library/a/business-operations-resume-guide; joinleland.com/library/a/google-bizops; igotanoffer.com/en/advice/bizops-interview-prep; tryexponent.com/blog/ace-the-bizops-interview; resumegeni.com/blog/operations-analyst-resume-guide; withresumeai.com/blog/resume-for-operations; beamjobs.com/resumes/operations-manager-resume-examples.
