# Changelog

## v1.1.1 - 2026-11-19

Fixes from an audit that followed README.md and SKILL.md literally on a clean machine.

- **Manual install that lands in the right place.** The old copy command put `SKILL.md` straight into `~/.claude/skills/` when that folder did not exist yet, so the skill never showed up. The README now creates the folder first and copies to `~/.claude/skills/edtech-vibe-coding`, with a PowerShell version for Windows and a way to check the result.
- **Claude.ai install.** Current path (Customize → Skills → "+" → Create skill → Upload a skill), and the note that Code execution and file creation must be on. The README says plainly that a Claude.ai upload covers the Idea and PRD stages only.
- **"What you need" section.** Claude Code, Node.js, git, a GitHub account, and for launch a VPS and a domain. `SKILL.md` step 2.2 now checks for `node`, `npm` and `git` before the prototype and installs what is missing.
- **Prompts that find their files.** S2.1, S2.6 and S4.11 said `references/...`, a path that exists in the skill folder and not in the user's project. They now name the skill.
- **Final security pass.** S4.11 asks for a review of the whole codebase. `/security-review` alone compares against GitHub and finds an empty diff once everything is pushed.
- **Deploy prompt.** S4.8 connects as root and runs the app as the site user, which matches the audit item "app not running as root".
- **Facts brought up to date.** Ubuntu 24.04 or 26.04 LTS. GDPR consent age given as 13 to 16 by country. COPPA entry rewritten from the FTC's own pages after the 2025 amendments, with links.
- **Checklist wired into the steps.** `SKILL.md` 2.2, 2.3 and 3.2 name the sections of `references/edu-checklist.md` they use.
- **Smaller things.** `SKILL.md` said the prompts ran to `S4.3`; it is `S4.13`. "40+ prompts" is now the real count, 35 numbered prompts in 45 copy blocks. Related skills section added. Long dashes replaced with hyphens. Byte-order mark removed from `.gitignore`.

## v1.1.0 - 2026-11-12

- Renamed to EdTech Vibe Coding (`edtech-vibe-coding`). Old links to `vibecode-pro-max-edu` redirect.
- Install in Claude Code: `/plugin marketplace add chuonglife/edtech-vibe-coding`, then `/plugin install edtech-vibe-coding@edtech-vibe-coding`.

## v1.0.0 - 2026-11-12

First public release, as Vibecode Pro Max for Education.

- 4-stage workflow: Idea → Spec & UI Design → Build → Launch.
- Copy-ready prompts S1.1 to S4.13.
- PRD and TDD templates for education apps, and a filled-in example (classroom quiz app).
- Education checklist: FERPA, COPPA, GDPR, WCAG 2.2 AA, assessment integrity, LTI 1.3 / OneRoster / SCORM / xAPI.
