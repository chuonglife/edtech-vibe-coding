# Prompt library — EdTech Vibe Coding

Copy-ready prompts for every step of the workflow. Replace `[brackets]`. Codes `S1.1 … S4.13` match the steps in `SKILL.md`.

## Contents
- Stage 1 — Idea: S1.1
- Stage 2 — Spec & UI: S2.1–S2.9
- Stage 3 — Build: S3.1–S3.12
- Stage 4 — Launch: S4.1–S4.13

---

## Stage 1 — Idea

### S1.1 Capture and test the idea
```text
I have an idea for an education app: [one or two sentences].
It is for [learners / teachers / parents / trainers] in [K-12 / university / bootcamp / corporate training / private tutoring].
Today they use [current tool or process].

1. Restate the problem in one sentence.
2. List the 3–5 existing tools that already solve something similar and what gap each leaves.
3. Tell me honestly whether building this is worth it, and what the smallest useful first version would be.
```

## Stage 2 — Spec & UI design

### S2.1 Create the PRD by AI interview
Switch to Plan mode (read-only) first.
```text
I need a PRD for my project. Use the template in references/prd-template.md.

MATERIALS I ALREADY HAVE (paste or attach everything — the more you get, the fewer questions you ask):
[description in my own words, current workflow, gradebook or attendance spreadsheet, rubric, syllabus, paper forms, meeting notes, messages from teachers or parents, screenshots of the tool we use today]

STEP 1 — Read first, ask nothing yet
Read all materials and fill every template section they already answer.
Report briefly: what you understood (bullets by template section) and what is missing, vague or contradictory.
Do not ask about anything already answered. With no materials, start from the Overview.

STEP 2 — Interview the gaps
Order questions by template section, most important first. Ask one, wait for my answer, then ask the next.
Each question comes with your suggested answer so I can reply "ok" or correct it.
Make sure to cover: learner age (any under 13?), roles and who sees whose data, high-stakes grades or certificates, sign-in with school Google/Microsoft accounts, devices and bandwidth, accessibility needs, languages.

STEP 3 — When I describe a feature
Single action:
• User Story: "As a [role], I want [action], so that [reason]"
• Priority: Must / Should / Nice — ask me, don't decide
• Done when: [testable conditions with numbers, described as what the user sees and can do — no adjectives]

Multi-step flow:
• User Story: "As a [role], I want [overall goal], so that [reason]"
• Priority: Must / Should / Nice — ask me
• Steps to complete: [1 → 2 → 3]
• Done when: [pass/fail conditions the user can check — do not restate the steps]
• Edge cases: [on failure → what happens, e.g. connection lost mid-quiz, late submission]

Confirm each part with me before recording it.

STEP 4 — After each group of features
Ask: "Any other features?" — until I say that's all.

STEP 5 — Produce the PRD
Present the plan for approval (we are in Plan mode). After I approve, write docs/PRD.md following the template.
Each feature is a level-3 heading (###) starting with 📝 Draft so the outline lists every feature.
Do not add features I did not confirm.

Start with STEP 1.
```

### S2.2 Review the PRD
Run with the strongest model available.
```text
Here is my PRD: docs/PRD.md

Act as a senior product manager who has shipped edtech products. Review it and point out:
1. Sections that are missing or too vague for an AI to implement
2. "Done when" lines without numbers, or that a user could not check alone
3. Important edge cases and error states not covered
4. Hidden assumptions that are not written down
5. Features that may conflict when implemented
6. Privacy, safeguarding and accessibility gaps for this audience

Raise one point at a time. After I answer each point, update the PRD.
```

### S2.3 First clickable prototype
```text
Read docs/PRD.md. Build a UI-only prototype in ui-demo/ with React (Vite) + Tailwind CSS — no backend. Pick a component library if it helps.

Make header, navigation and repeated blocks shared components; each screen is its own page and I can click between screens.

Start with the most important screen for the main role: [e.g. teacher dashboard / student "today" view].

Reference (optional): [link or screenshot]
Style I want: [e.g. calm, bright, large readable text, friendly for 10-year-olds / professional for corporate trainees]

Meet WCAG 2.2 AA: contrast, keyboard navigation, visible focus, no meaning by colour alone.
Use sample data only. When done, run it and open it for me.
```

### S2.4 Refine and complete the screens
```text
Fix every comment I just left on the interface in the browser. Reopen the page when done. If a comment is really a missing feature (not just a visual issue), add it to docs/PRD.md first, then build it.
```
```text
Adjust this screen: [e.g. bigger Submit button bottom-right, add a "Late" column to the gradebook, softer background].
```
```text
The main screen is approved. Build [2–3 screens, e.g. course page, quiz player, parent view] in the same style, reusing existing components. Repeat until every screen in the PRD exists, including one for each role.
```

### S2.5 Lock technical decisions (AI decides)
Use the strongest model for S2.5–S2.7.
```text
Here is my PRD: docs/PRD.md

Before writing the TDD, lock the technical decisions:
1. Ordinary technical choices (framework, libraries, code structure, storage): DECIDE YOURSELF, choosing the common, stable option that suits one person building with AI and running on a VPS. Do not ask me.
2. Only ask me what a non-specialist can answer and what affects how the app is used: number and type of users, sensitive data (grades, special-needs notes, data about minors), monthly budget, phone or computer, school Google/Microsoft sign-in, where data must be stored.
3. Each question at most 3 lines, plain words, no jargon, with your recommendation so I can answer "Agree" or pick another. One at a time.
4. Then summarise the decisions in at most 10 lines.
```

### S2.6 Write the full TDD
```text
Write docs/TDD.md using references/tdd-template.md.

Base it on docs/PRD.md and the decisions we locked. Choose technology by the app type in the PRD. Reuse the prototype in ui-demo/.
Include server-side role checks for every read and write, an audit log for grade changes, and data retention/deletion rules.

The "Summary for the project owner" is plain language, at most 10 lines.
```

### S2.7 Review the TDD (optional)
```text
Here is the TDD: docs/TDD.md

Review it as a senior developer, but DECIDE every technical issue yourself — do not ask me technical questions:
1. Edit the TDD directly where a fix is clearly needed (unclear logic, missing error cases, security or performance risks, missing access checks).
2. Report in at most 10 plain-language lines: one change per line + why.
3. Only ask me about cost, who may see which data, or where data is stored. Each question with a recommendation.
```

### S2.8 Give every feature a code
```text
In my PRD, prefix every feature and user story with a short code — no extra table, no separate list.

Convention:
- 3 capital letters by feature area, derived from the PRD (e.g. CRS courses, ENR enrolment, QUZ quizzes, GRD grades, ATT attendance)
- Optional sub-prefix: GRD.EXP
- Two-digit number: -01, -02

Level-3 heading, status first, code second:
### ⏳ [QUZ-01] Teacher creates a multiple-choice quiz

Keep the PRD structure; only add the codes.
```

### S2.9 Statuses and build order
```text
Statuses (at the start of each feature heading):
📝 Draft | ⏳ To do | 🔄 In progress | ⚠️ Partly done | ✅ Done

Example: ### 🔄 [ENR-02] Student joins a class with a code

Change all confirmed features from 📝 to ⏳, then order them by dependency (what must exist first) and by priority.
```
Note: level-4 headings do not show in the document outline — keep features at level 3.

## Stage 3 — Build

### S3.1 Get to know the workspace
```text
Open this project folder and explain briefly what each main folder is for. Then run the app in dev mode and open it in the browser for me.
```

### S3.2 Put the docs in the repo
```text
Create a docs/ folder and put PRD.md and TDD.md in it.
```

### S3.3 Write CLAUDE.md
```text
Create CLAUDE.md for this project with the content below (do NOT use @file imports, to avoid auto-loading):

# Project documents
Read when needed, not every time:
- PRD (product requirements): docs/PRD.md
- TDD (technical design): docs/TDD.md
- UI demo (approved prototype): ui-demo/

# Implementation rules
- Before coding a user story: read it in the PRD and the related TDD section
- Meet every "Done when" line of the story
- The status sits at the start of the feature heading (###) in the PRD: ⏳ → 🔄 → ✅ / ⚠️
- Follow the TDD for every technical choice: stack, DB schema, API design
- Read ui-demo/ before writing layout — reuse existing components, do not invent new layouts
- Enforce role and ownership checks on the server for every read and write
- Ask before acting if the PRD or TDD is unclear

# Commands
[dev / build / test commands]
```

### S3.4 Scaffold the project
```text
Read docs/PRD.md, docs/TDD.md and ui-demo/, then scaffold the codebase and dev environment exactly per the stack in the TDD.
```

### S3.5 Connect GitHub
```text
Here is the GitHub repository: [URL]. Connect it to this project folder.
```

### S3.6 Build a feature
```text
Build the next ⏳ feature in docs/PRD.md (or code: [leave blank to let the AI choose]).

Set it to 🔄, meet every "Done when" line, run and fix it yourself. Then set it to ✅ (or ⚠️ with what is missing) and report briefly what you did.
```

### S3.7 Accept against "Done when"
```text
Check feature [code] against each "Done when" line in docs/PRD.md: open the app in the browser and try it as a real user — log in as [teacher], then as [student] — take one screenshot per line and mark Pass / Fail. Fix any failure and re-check.
```
```text
On screen [X], as [role], I did [Y] and got: [description / screenshot]. Check the browser and logs, find the cause, fix it, then re-test.
```

### S3.8 Security review
```text
/security-review
```
Then:
```text
Fix every serious vulnerability found. Pay special attention to one learner reading or changing another learner's data and to students reaching teacher or admin actions. Confirm the feature still works, then report briefly what you fixed.
```

### S3.9 Commit and push
```text
Commit and push this feature to GitHub.
```

### S3.10 Before autonomous mode
```text
Before working autonomously:
1. Commit all current changes.
2. Switch to Auto mode.
3. Model: the strongest for work with many writes/deletes; a lighter one for easy, low-risk work.
```

### S3.11 Hand over a group of features
```text
/goal Every feature [codes, or "Must"] in docs/PRD.md is ✅ or ⚠️ with a note, each one self-checked against "Done when" and committed — or stop after 30 turns.
```
```text
Build these ⏳ features from docs/PRD.md one by one: [codes, or "all Must features"].

For each: 🔄 → meet "Done when" → run and fix → commit → ✅ or ⚠️.
If the PRD is unclear, write down the question and move on to another feature — never guess.

Finish with a table: code — status — note — question for me.
```

### S3.12 Accept a batch + review
```text
/code-review
```
```text
/security-review
```
```text
Fix the serious issues found, then commit.
```

## Stage 4 — Launch

### S4.1 Understand the architecture
```text
Briefly explain how a full-stack app runs on a VPS: domain, DNS, reverse proxy (Nginx/CloudPanel), the app's internal port and the database. Draw a text diagram.
```

### S4.2 Choose where to deploy
```text
My app: [database or not, expected users, budget, data-residency rules from the school]. Should I use Vercel/Netlify/Cloudflare Pages, a managed platform, or my own VPS? Explain briefly.
```

### S4.3 Prepare the VPS
```text
I just created an Ubuntu 24.04 VPS at [provider], [CPU/RAM], IP [IP]. Give me the checklist of what to do right away to prepare it for deploying the app.
```

### S4.4 Point the domain
```text
How do I point [domain] to the VPS at [IP]: the A record, and what TTL to use?
```

### S4.5 SSH key
```text
Set up SSH key login to the VPS at [IP] so I am not asked for a password each time (ssh-copy-id).
```

### S4.6 Install CloudPanel
```text
Install CloudPanel on the Ubuntu VPS [IP] (SSH key). Then show me how to log in, add a site, and how the reverse proxy points a domain to the app port.
```

### S4.7 Final review before going live
```text
/code-review
```
```text
Review the whole project before going live, focusing on sign-in and roles, grades and certificates, payments, data deletion and the database structure. List issues by severity and fix the serious ones.
```

### S4.8 Deploy in one prompt, then verify
```text
Deploy the app to [domain] on VPS [IP] as root with the SSH key. CloudPanel is installed — create a reverse-proxy site to the app (pick a free internal port, avoid 3000), install Node.js, PM2 and PostgreSQL, create .env, run the database migrations, build and enable SSL.
```
```text
Verify the deployment on [IP] / [domain]: PM2 status, valid HTTPS, database connection, all migrations applied, main page loads without errors. Then try the main flow as a teacher and as a student. Report item by item.
```

### S4.9 Full security audit
```text
Run a FULL security audit of production on VPS [IP] / [domain], group by group:
1. Secrets & passwords: no defaults or weak ones, .env not in git, strong secret keys
2. File permissions & users: .env chmod 600, app not running as root
3. Network & ports: only 80/443/SSH open (UFW), database not reachable from the internet
4. HTTPS/TLS: HTTPS enforced, HTTP→HTTPS redirect, TLS 1.2+
5. Security headers: HSTS, CSP, X-Content-Type-Options, X-Frame-Options; X-Powered-By off
6. App vulnerabilities: SQL injection, XSS, CSRF, auth bypass, input validation, IDOR on learner records
7. CORS: no Access-Control-Allow-Origin: *
8. Error handling: no stack traces, paths or versions exposed
9. Rate limiting on the API, especially sign-in and quiz submission
10. Dependencies with known CVEs
11. Database backups
For each issue: severity + fix.
```

### S4.10 Close ports and lock .env; secure the panel
```text
On VPS [IP]: close unneeded ports with UFW (keep 80, 443 and the SSH port) and set .env to permission 600.
```
```text
Secure the CloudPanel admin on VPS [IP]: set a custom domain panel.[domain] instead of [IP]:8443, then close port 8443 in the firewall.
```

### S4.11 Headers + education checks
```text
Add security headers (HSTS, X-Content-Type-Options, …) and disable X-Powered-By. Then run /security-review one last time, and go through references/edu-checklist.md (privacy notice, consent, data export/deletion, accessibility spot-check), reporting each item as Done / Missing.
```

### S4.12 Automatic backups + restore test
```text
On VPS [IP], set up automatic daily backups of the [app name] database, keep the 7 most recent, and store an extra copy off the VPS at [Google Drive / S3 / another server]. Then restore the latest backup into a temporary database to prove it works, and report the result.
```

### S4.13 Update a live app without losing data
```text
Update the app on VPS [IP] / [domain] to the latest version on GitHub.

Mandatory order:
1. Back up the database first
2. Pull the code, install packages, build
3. Run database migrations — never drop or recreate the database
4. Restart the app, check the main page and the new feature

Report each step. If anything fails, stop and ask me; do not improvise on real data.
```

🎉 The app is live, on its own domain with HTTPS. Distribution and growth come next, once it is stable and has real users.
