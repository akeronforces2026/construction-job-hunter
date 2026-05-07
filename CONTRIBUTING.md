# Contributing

This skill works better the more students use it and contribute back. If you find a way to improve it, please share.

## Things that genuinely help

- **Better STAR examples in the CV / cover letter templates.** The placeholders are deliberately generic. If you've written a great real-world bullet (anonymised, no specific contractor names), consider swapping it in as the new placeholder.
- **Additional graduate employers.** The list in `shared/graduate_employers.md` isn't exhaustive. If you know a regional contractor or specialist firm with a strong grad scheme, add them.
- **Better fit-score calibration.** If you've applied to a role you scored 80 and were rejected straight away (or scored 50 and got an offer), the rubric might be off. Open an issue with details.
- **Discipline-specific keyword additions.** If you're on a niche course (Architectural Tech, Building Surveying, MEP), add the regulatory and software keywords specific to your specialism.
- **University-specific tips.** If you've found a great careers service link, alumni network, or local employer connection at your uni, share it (in `shared/job_sites.md` under "University Careers Service" — generic enough to be useful to others).
- **Better interview question STAR skeletons.** If you've answered a tricky behavioural question well, the structure might help the next student.
- **Bug fixes.** Typos, broken URLs, outdated information — all worth flagging.

## Things to keep out

- **Personal information.** Don't commit your CV, your application log, your name, your university grade. The `.gitignore` covers most of this; double-check before pushing.
- **Specific contractor names in CV examples.** Use `[Contractor]` or `[Tier 1 Contractor]` rather than naming firms in placeholder examples — reduces awkwardness if a future student happens to be applying to that firm.
- **Private interview questions you signed an NDA for.** Some assessment centres ask you not to share specifics — respect that.
- **Anything that breaks the no-fabrication rule.** This is the cornerstone of the skill. If a contribution makes it easier to invent experience, it doesn't go in.

## How to contribute

### If you're comfortable with Git

1. Fork the repo on GitHub
2. Make your changes on a feature branch
3. Commit with a clear message ("Add X regional contractor to graduate_employers.md")
4. Open a pull request — explain what you changed and why
5. The maintainer will review, possibly suggest tweaks, and merge

### If you're not

1. Open an Issue on the repo
2. Describe what you want to change and why
3. Paste the proposed text directly into the issue
4. Someone will incorporate it

Both routes work. Don't feel you need Git fluency to contribute.

## Style guidance

- **Plain markdown** — these files render in many places (GitHub, ChatGPT Knowledge, Gemini Files). Stick to standard markdown.
- **British English** — the skill is UK-specific so the spelling and terminology should match.
- **Specific over generic** — "Mace's Battersea Phase 4 fit-out" is more useful than "a major project at a tier 1".
- **Honest tone** — no marketing fluff, no "amazing opportunity" filler. Students can spot it instantly.
- **Examples marked as placeholders** — if you add a new example, mark it with `[REPLACE WITH YOUR OWN]` so future students know it's swappable.

## Updating the .skill file

If you edit anything in `shared/` or `claude/SKILL.md`, the prebuilt `.skill` file in `claude/` is now out of date.

The maintainer will rebuild and commit a fresh `.skill` after merging your PR. If you want to rebuild it yourself before submitting, see `claude/README.md` → Rebuilding section.

## Code of conduct

Be kind. This is built by students, for students, in their own time. Disagreements about content are normal — disagreements that get personal aren't.

Thanks for making this better.
