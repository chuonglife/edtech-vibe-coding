# PRD - QuickCheck (example)

> A short example of the expected level of detail. Not a complete PRD.

## 1. Overview
- **One-sentence pitch:** QuickCheck helps middle-school teachers run 5-minute exit-ticket quizzes so they know before the next lesson which topics the class has not understood.
- **Problem today:** Teachers use paper slips; sorting 30 slips takes 20 minutes, so it happens once a month instead of every lesson.
- **Success in 3 months:** 5 teachers run at least 3 quizzes a week; time from last answer to class summary under 1 minute.

## 2. Setting and learners
- K-12, ages 11-14 → **users under 13: yes** (school-managed accounts, no self sign-up).
- Classes up to 35; school Chromebooks and some phones; Wi-Fi sometimes slow.

## 3. Roles
| Role | Can see | Can do | Cannot |
|---|---|---|---|
| Teacher | own classes, all their students' answers | create quizzes, open/close them, view summary | see other teachers' classes |
| Student | own answers and feedback | join with code, answer, see own result | see classmates' answers or names on results |

## 5. Features

### ⏳ [QUZ-01] Teacher creates a multiple-choice quiz
- **User story:** As a teacher, I want to create a quiz of up to 5 questions in under 3 minutes, so that I can use it at the end of today's lesson.
- **Priority:** Must
- **Done when:**
  - A quiz with 5 questions, 4 options each and one correct option can be saved in ≤ 3 minutes by a first-time teacher.
  - Saving with a question that has no correct option shows an error naming that question.
  - The quiz appears at the top of the teacher's quiz list immediately after saving.

### ⏳ [ENR-01] Student joins a live quiz with a code
- **User story:** As a student, I want to join with a 6-character code, so that I can start without remembering a password.
- **Priority:** Must
- **Steps to complete:** 1. Teacher opens the quiz → a 6-character code is shown. 2. Student enters the code on the home page. 3. Student picks their name from the class list (school-managed accounts) and starts.
- **Done when:**
  - A student reaches question 1 in ≤ 3 taps after typing the code.
  - A wrong code shows "Code not found" and keeps the typed text.
  - A closed quiz shows "This quiz has ended" instead of the questions.
- **Edge cases:**
  - Connection lost mid-quiz → answers saved so far are kept; on reconnect the student resumes at the next unanswered question.
  - Same student opens it on two devices → the second device shows "You are already taking this quiz".

### ⏳ [GRD-01] Class summary for the teacher
- **User story:** As a teacher, I want a per-question summary, so that I know which topic to re-teach tomorrow.
- **Priority:** Must
- **Done when:**
  - Within 60 seconds of closing the quiz, each question shows the % correct and the most chosen wrong option.
  - Questions under 60% correct are marked with an icon and the text "Re-teach", not by colour alone.
  - The summary can be exported as CSV with one row per student.

## 6. Data and privacy
- Collected: student first name + last initial, class, answers. No email, no birth date for students.
- Answers deleted automatically 12 months after the end of the school year; teacher can delete a class at any time.
- Consent handled by the school (school-managed accounts); no third-party analytics; no student data sent to AI APIs.

## 9. Out of scope (v1)
- Open-text questions, parent accounts, LMS integration.
