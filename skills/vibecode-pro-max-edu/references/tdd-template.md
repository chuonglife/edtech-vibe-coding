# TDD — [App name]

> Technical Design Document. Based on `docs/PRD.md` and the prototype in `ui-demo/`.

## 0. Summary for the project owner (plain language, max 10 lines)
1. What we are building, in one sentence.
2. Where it runs and what it costs per month.
3. How people sign in.
4. Where student data is stored and who can see it.
5. How we back up and how fast we can recover.
6. What is deliberately left for later.

## 1. App type and stack
- **App type:** web app / mobile app / desktop / chatbot tutor / mixed
- **Frontend:** [e.g. Next.js + React + Tailwind, reusing ui-demo components]
- **Backend:** [e.g. Next.js route handlers / Node API]
- **Database:** [e.g. PostgreSQL + Prisma/Drizzle migrations]
- **Hosting:** [VPS + CloudPanel / managed platform], region [ ]
- **Why this stack:** [2–3 lines: common, stable, easy for one person + AI]

## 2. Architecture
```
User → domain → DNS → reverse proxy (Nginx) → app :[port] → PostgreSQL
                                           ↘ file storage (assignments, media)
```

## 3. Data model
| Table | Key fields | Belongs to | Notes |
|---|---|---|---|
| users | id, role, email, name | organisation | |
| classes / courses | id, title, term | organisation | |
| enrolments | user_id, class_id, role_in_class | class | |
| assessments | id, class_id, type, due_at | class | |
| submissions | id, assessment_id, user_id, score | user | |
| grade_audit | submission_id, old, new, changed_by, at | submission | every grade change |

## 4. Access control
- Every read and write checks **role** and **ownership/enrolment on the server** (never only in the UI).
- Learners: only their own submissions, grades and profile.
- Teachers: only classes they teach.
- Parents: only linked children.
- Admins: their organisation only.
- IDs in URLs are never trusted on their own (prevents IDOR).

## 5. API / server actions
| Action | Who may call | Input | Output | Errors |
|---|---|---|---|---|

## 6. Integrations
[Sign-in provider, LTI 1.3 / OneRoster / xAPI if any, email, payments — with what data is shared]

## 7. Privacy and compliance
- Data minimisation: [what we do not collect]
- Retention and deletion jobs: [ ]
- Export on request: [format]
- Consent records: [ ]
- Regulations in scope: [FERPA / COPPA / GDPR / local law]

## 8. Security
- Secrets in `.env` (chmod 600, never committed), strong generated keys
- Passwords hashed (argon2/bcrypt) or delegated to SSO
- Rate limiting on sign-in, join-code and quiz-submission endpoints
- Security headers, CSP, HTTPS only
- `/security-review` every feature round; full audit before launch

## 9. Error handling and edge cases
[connection lost during a quiz (autosave), late submission, duplicate enrolment, deleted class, clock differences around deadlines]

## 10. Performance
[peak load, e.g. 300 concurrent quiz takers; caching; indexes]

## 11. Backups and updates
- Daily DB backup, keep 7, one copy off-server, restore tested
- Update order: backup → build → migrate (never drop) → restart → check

## 12. Testing
- Acceptance: each PRD "Done when" line, tested per role with screenshots
- Automated: [unit / integration / end-to-end tools]

## 13. Out of scope / later
- [ ]
