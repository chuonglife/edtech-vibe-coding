---
name: vibecode-pro-max-edu
description: 4-stage spec-first workflow (Idea → Spec & UI Design → Build → Launch) for building a NEW education or training app from scratch with Claude Code (LMS, course platform, quiz or assessment tool, gradebook, attendance tracker, tutoring, corporate training or student portal). Produces a PRD and TDD in the repo, a clickable React prototype before real code, a per-feature loop with acceptance checks and security review, and a hardened VPS deploy with backups, plus checks for student privacy (FERPA, COPPA, GDPR), WCAG 2.2 AA, roles and assessment integrity. Use whenever someone wants to start a brand-new app or tool for teaching, learning, schools, universities, tutors or L&D teams, even if they only say "build an app for my class", "e-learning platform idea", "quiz app for my students" or "vibecode". Not for adding features to an existing codebase.
---

# Vibecode Pro Max for Education — from idea to a live learning app

A disciplined vibe-coding workflow for people who build tools for teaching and learning: teachers, instructional designers, training managers, edtech founders, school IT staff. It turns an idea into a deployed app through four stages and eleven steps, and it keeps the decisions in files, not in chat history.

## Bundled references (read only when the step needs them)
- `references/prompts.md` — copy-ready prompts for every step, numbered `S1.1` … `S4.3`. Open it when you need the exact wording to give the user, or when writing course material.
- `references/prd-template.md` — the PRD template, with education-specific sections (learners, roles, learning outcomes, data about minors).
- `references/tdd-template.md` — the TDD template, starting with a 10-line "Summary for the project owner".
- `references/edu-checklist.md` — privacy, accessibility, assessment-integrity and interoperability checks (FERPA, COPPA, GDPR, WCAG 2.2 AA, LTI 1.3, SCORM, xAPI, OneRoster). Use it in Stage 2.1, 2.3, 3.2 and 4.2.
- `references/example-prd-quiz-app.md` — a short filled-in PRD for a classroom quiz app, to show the level of detail expected.

## Why this workflow exists
Projects built by "just prompting" fail in the same three places:
1. **No PRD or TDD saved as real files.** Decisions live only in the conversation and are lost at the next session.
2. **No UI design before production code.** The data model gets built around guesses, then rebuilt when the teacher finally sees the screen.
3. **Security left to a big audit at the end.** By then a student can already see another student's grades, or an API key is exposed in the frontend.

Education apps raise the cost of all three: they hold data about children and young people, grades and assessment results that matter, and they are used by people (teachers, parents, older trainees) who have little patience for clumsy screens. This skill closes those gaps.

## Core behaviour (more important than the content of any step)
1. **Go in order: 1 → 2 → 3 → 4.** Skip a step only when the user asks and knows what is being skipped. Each step feeds the next; a skipped PRD becomes a confused TDD and a rewritten codebase.
2. **Ask before you assume.** Before each step, collect what is needed to finish that step. Use multiple-choice questions when the options are clear, open questions when you need a description. Always offer your own recommendation so the user can just say "ok".
3. **One step at a time.** Finish a step, show the result, then move on — unless the user says "do it all".
4. **Track progress** with the session's task list, at stage and step level.
5. **Never create files "just to have them".** If information is missing, ask.
6. **Speak the user's language.** Educators are experts in pedagogy, not in databases. Explain technical choices in plain words and translate their classroom vocabulary (cohort, term, rubric, gradebook, module) into the spec without making them learn yours.

## STAGE 1 — 💡 Idea
Capture the idea immediately. Then check whether a good solution already exists (Google Classroom, Moodle, Canvas, Kahoot, Quizlet, Notion templates, a spreadsheet…). If an existing tool solves 90% of the problem, say so honestly — building is only worth it if the gap is real. Clarify with the user:
- What teaching or training problem does it solve, and for whom (learner age, setting: K-12, higher ed, bootcamp, corporate L&D, private tutoring)?
- Why now, and what do they use today?
- Who pays, if anyone (school, parent, learner, employer)?

No file needed yet; summarise in the conversation.

## STAGE 2 — 📋 Spec and UI Design

### 2.1 Write the PRD (prompt S2.1, review prompt S2.2)
1. **Materials first, questions second.** Ask for everything the user already has: a description in their own words, the current process, spreadsheets (gradebooks, attendance sheets), paper forms, rubrics, syllabus, meeting notes, screenshots of the tool they use today. Read all of it and fill every section of `references/prd-template.md` that the materials already answer. Report briefly what you understood (by template section) and what is missing, vague or contradictory. Do not ask again about anything the materials already answer.
2. **Stay in Plan mode (read-only)** until the user approves; write no files yet.
3. **Interview the gaps** in template order, most important first, one question at a time, each with a suggested answer.
4. **Feature format.**
   - Single action → User Story ("As a [teacher/student/parent/admin], I want [action], so that [reason]") + Priority Must/Should/Nice (ask, do not decide) + **Done when** (testable conditions with numbers, written as what the user sees and can do — no adjectives like "fast" or "easy").
   - Multi-step flow → add **Steps to complete** (1 → 2 → 3) and **Edge cases** (what happens on failure: lost connection mid-quiz, late submission, duplicate enrolment).
   - Confirm each feature before recording it; after each group ask "any other features?".
5. **Education-specific questions** to make sure are answered (see `references/edu-checklist.md`): Are any users under 13 (COPPA) or under 16 in the EU (GDPR)? Which roles exist and who can see whose data? Are grades or certificates high-stakes? Does it need to integrate with an existing LMS or the school's Google/Microsoft accounts? Will learners use phones, shared computers, or low bandwidth?
6. **Write `docs/PRD.md`** when approved. Each feature is a level-3 heading (`###`) starting with the status 📝 Draft, so the document outline shows every feature. Add nothing the user did not confirm.
7. **Review the PRD with the strongest model available**, in the role of a senior product manager with edtech experience: missing or vague sections, "Done when" lines without numbers, missing edge cases and error states, hidden assumptions, conflicting features, and privacy or accessibility gaps. Raise one point at a time, then update the PRD.

### 2.2 Clickable prototype before real code (prompts S2.3, S2.4)
1. Read `docs/PRD.md` and build a UI-only prototype in `ui-demo/` with React (Vite) + Tailwind CSS, sample data only. Shared header, navigation and repeated blocks become reusable components; each screen is its own page and you can click between them. Start with the most important screen for the main role (usually the teacher dashboard or the learner's "today" view). If the user has a reference (link, screenshot), use it. Run it and open it in the app's browser pane for the user.
2. **Design for the real audience:** large tap targets and readable type for young learners and older trainees; contrast, keyboard navigation, focus states and reduced motion that pass WCAG 2.2 AA; no information conveyed by colour alone (red/green grades fail for colour-blind users). If a UI/UX skill is available, use it alongside this one and run its pre-delivery checklist.
3. **Feedback by comments on elements.** The user walks through every screen and leaves comments directly on the elements in the browser pane, then sends one prompt: fix all comments; any comment that is really a missing feature goes into `docs/PRD.md` first. Repeat until the main screen is right, then build the next 2–3 screens in the same style, reusing components, until every screen in the PRD exists — including the screen for each role.
4. **PRD ↔ UI loop.** When the UI reveals a gap in the PRD, update the PRD immediately; never let them drift apart until coding.

### 2.3 Technical design: TDD (prompts S2.5, S2.6, S2.7)
1. **Decide the technical details yourself.** Framework, libraries, code structure and storage: choose the common, stable option that suits one person building with AI. Ask the user only what a non-specialist can answer and what changes how the app is used: who uses it and how many, which data is sensitive (grades, special-needs notes, minors' data), monthly budget, phone or computer, sign-in with school Google/Microsoft accounts or not, where data must be stored (country or region). Each question at most 3 lines, plain words, with a recommendation; one at a time; summarise the decisions in at most 10 lines. Use the strongest model for this whole step — a wrong technical decision is expensive later.
2. **Write `docs/TDD.md`** from `references/tdd-template.md`. Pick technology by app type (web app, mobile, desktop, chatbot tutor), reuse the `ui-demo/` components. Must cover: role-based access control enforced on the server for every read and write, data retention and deletion, audit log for grade changes, and the integrations chosen. The "Summary for the project owner" at the top is plain language, at most 10 lines — it is the only part the user has to read.
3. **Review the TDD** as a senior developer who decides technical issues alone: fix the TDD directly, report at most 10 lines, and only ask about cost, who may see which data, and where data is stored.

### 2.4 Order the user stories inside the PRD (prompts S2.8, S2.9)
1. Prefix every feature with a short code: three capital letters by feature area derived from the PRD (e.g. `CRS` courses, `ENR` enrolment, `QUZ` quizzes, `GRD` grades, `ATT` attendance), optional sub-prefix (`GRD.EXP`), two-digit number. Example: `### ⏳ [QUZ-01] Teacher creates a multiple-choice quiz`. Status first, code second, still a level-3 heading.
2. Statuses: 📝 Draft | ⏳ To do | 🔄 In progress | ⚠️ Partly done | ✅ Done. Move confirmed features from 📝 to ⏳ and order them by dependency (accounts and roles before courses, courses before enrolment, enrolment before quizzes and grades). The PRD outline is the progress board; no separate stories file is needed.

## STAGE 3 — ⚙️ Build

### 3.1 Set up (prompts S3.1–S3.5)
1. **Environment.** Claude Code (desktop app Code tab, CLI or IDE). One task per session, named clearly. On Windows, WSL makes commands smoother. **Permission modes:** Plan (read-only, review the plan first) → edit automatically (normal work) → Auto (with safety filters; only once the project is in git). Avoid fully unrestricted modes on a machine with real data.
2. Put `docs/PRD.md`, `docs/TDD.md` and `ui-demo/` in the repo.
3. **Write a real `CLAUDE.md` without `@file` imports** (they load the files into context on every turn, which is slow and costly). List the paths so the AI reads them when needed. Content: where the docs are; implementation rules — before each story read it in the PRD and the related TDD section; meet every "Done when" line; update the status in the PRD heading; follow the TDD for every technical choice; read `ui-demo/` before writing layout and reuse components; enforce role checks on the server; ask if the PRD or TDD is unclear. Add the usual dev/build/test commands.
4. Scaffold the codebase and dev environment exactly per the TDD stack, reading `ui-demo/` too.
5. Connect the GitHub repository (ask for the URL).

### 3.2 The feature loop — repeat for each feature (prompts S3.6–S3.9)
Do the first few features one by one so the user learns how the AI works. Each round has four steps:
1. **Build.** "Build the next ⏳ feature in docs/PRD.md (or code X). Set it to 🔄, meet every 'Done when' line, run and fix it yourself, then set ✅ (or ⚠️ with what is missing) and report briefly." Plan mode is not needed for ordinary features; use it only for changes to real data or large multi-file changes.
2. **Accept against "Done when".** Let Claude open the app in the browser, try each line as the relevant role (log in as teacher, then as student), take one screenshot per line and mark Pass/Fail; fix and re-check failures. When the user finds a bug: "On screen X, as role R, I did Y and got Z (screenshot). Check the browser and logs, fix it, re-test."
3. **Security review.** Run `/security-review` on the changed code: injection, one learner reading another learner's data, a student acting as a teacher, secrets in code, vulnerable packages. "Fix every serious issue, confirm the feature still works, report briefly." Do this **every round**, never batch it — in education, the classic bug is a student changing an ID in the URL and seeing a classmate's grades.
4. **Save.** Commit and push to GitHub.

### 3.3 Let the AI build several features on its own (prompts S3.10–S3.12)
1. Before going autonomous: commit everything; choose Auto mode; choose the model — the strongest one for work with many writes or deletes, a lighter one for easy, low-risk work.
2. Hand over a group: `/goal Every feature [codes, or "Must"] in docs/PRD.md is ✅ or ⚠️ with a note, each one self-checked against "Done when" and committed — or stop after 30 turns.` Or in words: build them one by one (🔄 → meet "Done when" → test → commit → ✅/⚠️); when the PRD is unclear, write the question down and move to another feature instead of guessing; end with a table of code, status, note, question. Only do this once the PRD is clear — a vague PRD makes the AI fast and wrong. Watch usage with `/usage`.
3. Accept in one pass: read the table, answer the questions, try the ✅ features; after each group run `/code-review` then `/security-review`, "fix the serious issues and commit".

## STAGE 4 — 🚀 Launch

### 4.1 Deploy (prompts S4.1–S4.8)
1. **Understand the architecture:** User → domain → DNS → VPS → reverse proxy (CloudPanel/Nginx) → app (internal port) → database.
2. **Choose how to deploy:** an app with a database → a VPS (full control over student data, predictable cost) or a managed platform the school already trusts; a static landing page → Vercel, Netlify or Cloudflare Pages. If the school has data-residency rules, pick the server region accordingly.
3. **VPS baseline:** Ubuntu 24.04 LTS, start with 1 vCPU + 2 GB RAM, a region close to the users, automatic provider backups on. Point the domain with an A record to the VPS IP. Use an SSH key (`ssh-copy-id`) so the AI can work without passwords. CloudPanel (free, light) gives an Nginx reverse proxy to the app port, automatic Let's Encrypt SSL, several sites per server and a CLI (`clpctl`).
4. **Review at milestones, not after every edit:** once before going live, and whenever you touch sensitive areas — sign-in, roles and permissions, payments, grades and certificates, data deletion, database structure. Run `/code-review` then "review the whole project, list issues by severity, fix the serious ones".
5. **Deploy with one prompt:** create the reverse-proxy site, let the AI pick a free internal port (avoid 3000, it is usually taken), install Node.js, PM2 and PostgreSQL, create `.env`, **run the database migrations** (production must match local), build, enable SSL.
6. **Check after deploy:** PM2 status, valid HTTPS, database connection, migrations applied, main pages load; then walk through the main flow as each real role would.

### 4.2 Security after deploy (prompts S4.9–S4.11)
Audit all eleven areas: secrets and passwords (no defaults, `.env` never committed); file permissions and users (`.env` chmod 600, app not running as root); network and ports (UFW allows only 80/443/SSH, database never exposed); HTTPS/TLS (redirect, TLS 1.2+); security headers (HSTS, CSP, X-Content-Type-Options, X-Frame-Options, no X-Powered-By); app vulnerabilities (SQLi, XSS, CSRF, auth bypass, input validation); CORS not `*`; no stack traces in errors; API rate limiting (especially sign-in and quiz submission); dependencies with known CVEs; backups. For each issue give severity and the fix. Move the CloudPanel admin to a subdomain such as `panel.<domain>` and close port 8443. Then run the education checks in `references/edu-checklist.md` (privacy notice, parental consent where required, data export and deletion on request, accessibility spot-check). Repeat the full audit after every major infrastructure change.

### 4.3 Backups and safe updates (prompts S4.12, S4.13)
1. Automatic daily database backups, keep 7, one copy off the VPS; **test a restore** into a temporary database to prove it works. Grades and coursework are irreplaceable.
2. Update a live app in this order: backup → pull code, install packages, build → migrations (never drop or recreate the production database) → restart, check the main page and the new feature. On any error, stop and ask the user; never improvise on real data. Avoid deploying during exam periods or grading deadlines.

After 4.3, report to the user: which stages are done, which docs are in the repo, where the app runs. Distribution and growth (pricing, school sales, teacher communities) come later, once the app is stable and has real users.
