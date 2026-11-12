# Education checklist — privacy, accessibility, integrity, interoperability

Use in Stage 2.1 (ask), 2.3 (design), 3.2 (test each round) and 4.2 (audit before and after launch). This is practical guidance, not legal advice; when an app serves schools in a regulated market, the school's data-protection officer has the final word.

## Contents
1. Student data privacy
2. Safeguarding
3. Accessibility (WCAG 2.2 AA)
4. Assessment integrity
5. Interoperability
6. Classroom reality

## 1. Student data privacy
- [ ] **Know which rules apply.** US schools: FERPA (education records), COPPA (children under 13 online), state laws such as California's SOPIPA. EU/UK: GDPR / UK GDPR (children's consent age 13–16 depending on country). Elsewhere: the local data-protection law.
- [ ] **Minimise.** Collect only what a feature needs. No birth dates if age bands are enough; no home addresses for a quiz app.
- [ ] **Consent.** If users can be under 13 (or under the GDPR age), plan who gives consent — usually the school acting for parents, or verified parental consent.
- [ ] **No advertising or profiling** on student data; never sell or share it with third parties beyond the services needed to run the app.
- [ ] **Privacy notice** in plain language, reachable from every page.
- [ ] **Export and deletion on request**, and automatic deletion after the retention period.
- [ ] **Data residency** respected when the school requires it (choose server and backup regions to match).
- [ ] **Third-party processors listed** (hosting, email, analytics, AI APIs) and what each receives. Do not send identifiable student data to an AI API unless the school has agreed to it.

## 2. Safeguarding
- [ ] No unmoderated direct messages between adults and minors; teacher–student messages visible to the school.
- [ ] Reporting button for inappropriate content where users can post.
- [ ] Profile photos and display names reviewed or limited for young learners.

## 3. Accessibility (WCAG 2.2 AA)
- [ ] Text contrast ≥ 4.5:1 (≥ 3:1 for large text and UI components).
- [ ] Everything works by keyboard; focus is always visible and not hidden behind sticky headers.
- [ ] Tap targets at least 24×24 px (aim for 44×44 on phones).
- [ ] Meaning never by colour alone (grades, correct/incorrect answers use icons or text too).
- [ ] Images have alt text; videos have captions; audio has transcripts.
- [ ] Timed quizzes allow extended time per learner (accommodations).
- [ ] Respects reduced-motion settings; no flashing content.
- [ ] Works at 200% zoom and on a 320 px wide screen.
- [ ] Clear language; readable fonts; avoid walls of text for young readers.

## 4. Assessment integrity
- [ ] Grades and answers are computed and stored on the server, never trusted from the browser.
- [ ] Correct answers are not sent to the browser before submission.
- [ ] Deadlines checked with server time; late submissions flagged, not silently accepted or lost.
- [ ] Autosave during long quizzes; resume after lost connection.
- [ ] Every grade change logged (who, when, old value, new value).
- [ ] Optional: question shuffling, question pools, one attempt per learner.
- [ ] Certificates carry a verifiable ID or link if they are high-stakes.

## 5. Interoperability (only if the PRD needs it)
- **Sign-in:** Google Workspace for Education, Microsoft 365 (Entra ID), or the school's SAML/OIDC SSO.
- **LTI 1.3 / LTI Advantage:** launch the app from Canvas, Moodle, Blackboard, Brightspace; send grades back to the LMS gradebook.
- **OneRoster:** import classes and enrolments from the student information system.
- **SCORM / xAPI / cmi5:** package or track learning content across platforms.
- **QTI:** import/export quiz questions.

## 6. Classroom reality
- [ ] A teacher can set up a class in under 5 minutes; students join with a short code or link.
- [ ] Works on the oldest device in the room (low-end Chromebook, small phone) and on slow Wi-Fi.
- [ ] Peak load planned for the whole school logging in at the same minute.
- [ ] No deployments during exam periods or grading deadlines.
- [ ] Bulk actions for teachers (import roster from CSV, export grades to spreadsheet).
