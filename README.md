# EdTech Vibe Coding - Claude Code Skill for Building Education Apps

> Formerly published as `vibecode-pro-max-edu`; old links redirect here.

**EdTech Vibe Coding** is a free, open-source [Claude Code](https://claude.com/claude-code) skill (an Agent Skill) that guides teachers, instructional designers, training managers and edtech founders through building a **new education or training app from scratch with AI** - from idea to a secure, live web app - using a 4-stage, spec-first vibe coding workflow: **Idea → Spec & UI Design → Build → Launch**.

It works for any learning product: LMS, online course platform, quiz and assessment app, gradebook, class roster, attendance tracker, tutoring marketplace, corporate L&D portal, student or parent portal, school admin dashboard.

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
![Claude Code skill](https://img.shields.io/badge/Claude%20Code-Agent%20Skill-orange)
![Domain: Education](https://img.shields.io/badge/domain-education%20%26%20training-blue)
![WCAG 2.2 AA](https://img.shields.io/badge/accessibility-WCAG%202.2%20AA-purple)

---

## Key facts

| | |
|---|---|
| **What it is** | An Agent Skill (`SKILL.md` + references) for Claude Code. A Claude.ai upload covers the Idea and PRD stages only, because the later stages need local files, a dev server and SSH |
| **Who it is for** | Educators, instructional designers, L&D teams, school IT, edtech founders - no coding background required |
| **What you get** | A real PRD and TDD in your repo, a clickable React prototype, a tested app, a hardened VPS deployment with backups |
| **Workflow** | 4 stages, 11 steps, 35 numbered prompts in 45 copy-ready blocks |
| **Education-specific** | FERPA, COPPA and GDPR privacy checks; WCAG 2.2 AA accessibility; role-based access (admin, teacher, student, parent); assessment integrity; LTI 1.3, OneRoster, SCORM, xAPI guidance |
| **License** | MIT - free for personal, school and commercial use |

---

## Why use a workflow for vibe coding an education app?

AI can write an app in an afternoon. Most of those apps break in the same three places:

1. **No written spec.** Decisions live only in the chat and are gone next session. → This skill writes `docs/PRD.md` and `docs/TDD.md` into your repository.
2. **No design before code.** The database is built around guesses, then rebuilt when the teacher finally sees the screen. → You click through a full prototype and approve it before production code starts.
3. **Security at the very end.** By then a student can change an ID in the URL and see a classmate's grades. → A security review runs **every** feature round, plus a full audit before launch.

Education raises the stakes: the data belongs to children and young people, grades matter, and the users are busy teachers and parents. The skill bakes in the checks that matter for schools and training providers.

---

## The 4-stage workflow

| Stage | Steps | Output |
|---|---|---|
| **1. 💡 Idea** | Capture the idea, check existing tools (Google Classroom, Moodle, Canvas, Kahoot…), define the smallest useful version | Problem statement |
| **2. 📋 Spec & UI Design** | AI-interview PRD from your existing materials → senior-PM review → clickable React + Tailwind prototype in `ui-demo/` → TDD where the AI makes the technical decisions → feature codes and statuses | `docs/PRD.md`, `ui-demo/`, `docs/TDD.md` |
| **3. ⚙️ Build** | `CLAUDE.md` setup → feature loop: build → accept against "Done when" with screenshots per role → `/security-review` → commit → autonomous runs with `/goal` | Working, reviewed code on GitHub |
| **4. 🚀 Launch** | VPS + CloudPanel deployment in one prompt → 11-area security audit → education checklist → daily backups with a tested restore → safe updates | A live app on your domain with HTTPS |

Each feature in the PRD is a heading with a status and a code, so the document outline doubles as your progress board:

```markdown
### ✅ [QUZ-01] Teacher creates a multiple-choice quiz
### 🔄 [ENR-01] Student joins a live quiz with a code
### ⏳ [GRD-01] Class summary for the teacher
```

---

## What you need

- **Claude Code**, desktop app or CLI, with a Claude account that includes Claude Code. Install and account options: https://code.claude.com/docs/en/setup
- **Node.js LTS and git.** The prototype in Stage 2 is a React app and will not start without Node.js. If either is missing, Claude offers to install it. Say yes.
- **A free GitHub account** with an empty repository, from Stage 3 on. The per-feature `/security-review` needs the project to have a GitHub remote.
- **For launch (Stage 4): a VPS and a domain name.** A small server costs about US$5-12 a month. Nothing in Stages 1 to 3 needs them.

You do not need to know how to use any of these. You need to have them.

## Installation

### Option 1 - Claude Code plugin marketplace (recommended)
In Claude Code, run:

```text
/plugin marketplace add chuonglife/edtech-vibe-coding
/plugin install edtech-vibe-coding@edtech-vibe-coding
```

### Option 2 - Copy the skill folder
macOS, Linux or Git Bash:

```bash
git clone https://github.com/chuonglife/edtech-vibe-coding.git
mkdir -p ~/.claude/skills
cp -r edtech-vibe-coding/skills/edtech-vibe-coding ~/.claude/skills/edtech-vibe-coding
```

Windows PowerShell:

```powershell
git clone https://github.com/chuonglife/edtech-vibe-coding.git
New-Item -ItemType Directory -Force "$HOME\.claude\skills" | Out-Null
Copy-Item -Recurse edtech-vibe-coding\skills\edtech-vibe-coding "$HOME\.claude\skills\edtech-vibe-coding"
```

Check the result: the file `SKILL.md` must sit at `.claude/skills/edtech-vibe-coding/SKILL.md` in your home folder. Restart Claude Code and type `/skills`; `edtech-vibe-coding` should be in the list. These commands are for a first install. To update, delete that `edtech-vibe-coding` folder and run the copy line again.

### Option 3 - Claude.ai (Idea and PRD stages only)
1. In **Settings → Capabilities**, turn on **Code execution and file creation**. Skills do not run without it.
2. Download `edtech-vibe-coding.zip` from the [latest release](https://github.com/chuonglife/edtech-vibe-coding/releases/latest).
3. Open **Customize → Skills**, click **+**, then **Create skill**, then **Upload a skill**, and pick the zip.

On a Team or Enterprise plan an owner may have to allow code execution and skills first.

---

## Usage

Just describe what you want to build. The skill triggers on requests such as:

- *"Build me an app where my students can take a 5-minute quiz at the end of each lesson."*
- *"I have an idea for an e-learning platform for nurses' continuing education."*
- *"Vibe code an attendance tracker for our after-school program."*
- *"We need an internal training portal with courses, completion tracking and certificates."*

Claude then walks you through each stage, asks only what a non-specialist can answer (who uses it, which data is sensitive, budget, phone or computer), and decides the technical details itself.

### What's inside

```
skills/edtech-vibe-coding/
├── SKILL.md                         # the workflow and rules Claude follows
└── references/
    ├── prompts.md                   # 35 numbered prompts, S1.1 … S4.13
    ├── prd-template.md              # PRD with learners, roles, outcomes, privacy
    ├── tdd-template.md              # TDD with a 10-line owner summary
    ├── edu-checklist.md             # FERPA/COPPA/GDPR, WCAG 2.2 AA, integrity, LTI/OneRoster/SCORM/xAPI
    └── example-prd-quiz-app.md      # filled-in example: classroom exit-ticket quiz app
```

---

## FAQ

**What is vibe coding?**
Vibe coding means building software by describing what you want in plain language and letting an AI coding agent such as Claude Code write, run and fix the code. This skill adds the structure that keeps vibe-coded apps maintainable and safe.

**Do I need to know how to code?**
No. The skill is written for educators and trainers. Technical choices are made by the AI; you are asked only about things you know better than anyone - your learners, your classroom and your budget.

**Which apps can I build with it?**
Any new education or training app: LMS, course platform, quiz and assessment tool, gradebook, attendance tracker, flashcards, tutoring booking, certification portal, parent communication app, school dashboard.

**Does it help with student data privacy laws?**
Yes. The PRD template asks about learner age and consent, the TDD enforces server-side role checks and grade-change audit logs, and `edu-checklist.md` covers FERPA, COPPA and GDPR practices. It is practical guidance, not legal advice.

**Is the result accessible?**
The prototype and acceptance steps target WCAG 2.2 AA: contrast, keyboard navigation, visible focus, captions, extended time for timed quizzes, and no meaning conveyed by colour alone.

**Can it integrate with Canvas, Moodle or Google Classroom?**
The skill covers sign-in with Google Workspace for Education and Microsoft 365, and gives guidance for LTI 1.3, OneRoster, SCORM, xAPI and QTI when your PRD needs them.

**Can I use it to add features to an existing app?**
It is designed for new projects starting from zero. Many prompts (feature loop, security review, safe updates) still work on existing projects.

**How much does hosting cost?**
The default deployment is a small VPS (1 vCPU, 2 GB RAM, Ubuntu 24.04 or 26.04 LTS) with free CloudPanel and free Let's Encrypt SSL - typically around US$5-12 per month.

---

## Related skills

This skill builds apps. If you are building the course itself, five sibling skills cover that line, from program to video:

- [Curriculum Designer](https://github.com/chuonglife/curriculum-designer-skill): the whole training program, modules and lessons with objectives and hours.
- [Lesson Content Writer](https://github.com/chuonglife/lesson-content-writer-skill): one complete lesson with measurable objectives and a word-for-word script.
- [Lesson Slide Designer](https://github.com/chuonglife/lesson-slide-designer-skill): the slide deck and the video script for a lesson.
- [Lesson Video Producer](https://github.com/chuonglife/lesson-video-producer-skill): the narrated video from those slides.
- [Lesson Assessment Designer](https://github.com/chuonglife/lesson-assessment-designer-skill): the quiz, test and rubric from a lesson's objectives.

## Credits

The 4-stage workflow is adapted from the Vietnamese **Vibe Code Roadmap v2** by [class.mecode.pro](https://class.mecode.pro), extended with lessons from running production apps and with education-specific guidance. English edition and education adaptation by [@chuonglife](https://github.com/chuonglife).

## Contributing

Issues and pull requests are welcome - especially new example PRDs (gradebook, LMS, tutoring), translations, and country-specific privacy notes.

## License

[MIT](LICENSE)

---

*Keywords: Claude Code skill, Agent Skills, vibe coding, AI app builder for teachers, edtech development workflow, build an LMS with AI, quiz app, e-learning platform, PRD template, TDD template, FERPA, COPPA, GDPR, WCAG 2.2, LTI 1.3, instructional design, corporate training, no-code for educators.*
