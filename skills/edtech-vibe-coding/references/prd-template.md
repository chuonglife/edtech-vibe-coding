# PRD — [App name]

> Product Requirements Document. Status of each feature sits at the start of its `###` heading: 📝 Draft | ⏳ To do | 🔄 In progress | ⚠️ Partly done | ✅ Done.

## 1. Overview
- **One-sentence pitch:** [App] helps [who] to [do what] so that [outcome].
- **Problem today:** [what goes wrong with the current tool or process, with a real example]
- **Why now:** [deadline, new term, policy change, growth]
- **Success in 3 months:** [measurable, e.g. "5 teachers run weekly quizzes; grading time per quiz drops from 40 to 10 minutes"]

## 2. Setting and learners
- **Education setting:** K-12 / higher education / bootcamp / corporate L&D / private tutoring / other
- **Learner age range:** [e.g. 11–14]. Any users under 13? Under 16 in the EU? → yes / no
- **Class or cohort size:** [typical and maximum]
- **Devices and connectivity:** [school Chromebooks, personal phones, shared lab PCs, low bandwidth, offline needed?]
- **Languages:** [UI languages, right-to-left needed?]
- **Accessibility needs known today:** [screen readers, dyslexia-friendly fonts, captions, extra time on tests]

## 3. Roles and permissions
| Role | Can see | Can do | Cannot |
|---|---|---|---|
| Admin | | | |
| Teacher / trainer | | | |
| Student / learner | only their own work and grades | | see other learners' data |
| Parent / guardian (optional) | | | |

## 4. Learning outcomes and pedagogy (if the app teaches or assesses)
- **Outcomes the app supports:** [e.g. "students practise 20 vocabulary items per week"]
- **Assessment type:** formative / summative / certification. High-stakes? → yes / no
- **Grading model:** points, percentage, rubric, pass/fail, mastery levels
- **Feedback to learners:** [immediate, after deadline, teacher comments]

## 5. Features
Group features by area. Each feature is a level-3 heading.

### 📝 [Feature name — single action]
- **User story:** As a [role], I want [action], so that [reason].
- **Priority:** Must / Should / Nice
- **Done when:**
  - [testable condition with a number, described as what the user sees and can do]
  - [...]

### 📝 [Feature name — multi-step flow]
- **User story:** As a [role], I want [overall goal], so that [reason].
- **Priority:** Must / Should / Nice
- **Steps to complete:** 1. … → 2. … → 3. …
- **Done when:**
  - [pass/fail condition the user can check]
- **Edge cases:**
  - [failure] → [what happens]

## 6. Data and privacy
- **Personal data collected:** [names, emails, grades, attendance, special-needs notes, photos, voice]
- **Sensitive or about minors:** [list]
- **Who owns the data:** school / company / learner
- **Retention and deletion:** [e.g. delete a class's data 12 months after the course ends; learner can request export and deletion]
- **Consent:** [parental consent needed? who collects it?]
- **Where data must be stored:** [country / region, if required]

## 7. Integrations
- **Sign-in:** email + password / Google Workspace for Education / Microsoft 365 / school SSO
- **LMS or SIS:** none / LTI 1.3 tool in Canvas, Moodle, Blackboard / OneRoster roster sync
- **Content standards:** SCORM / xAPI / Common Cartridge — needed?
- **Other:** [payments, email, video, calendar]

## 8. Non-functional requirements
- **Users at the same time:** [e.g. 300 students taking a quiz at 9:00]
- **Availability:** [e.g. must not go down during exam weeks]
- **Accessibility target:** WCAG 2.2 AA
- **Budget per month:** [amount]

## 9. Out of scope (for this version)
- [things explicitly not built now]

## 10. Open questions
- [question] — owner — due date
