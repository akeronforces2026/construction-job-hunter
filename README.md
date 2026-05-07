# Student Construction Job Hunter

A free, open, model-agnostic skill for **UK university construction students** at any year level — built for graduate schemes, year-in-industry placements, and summer internships across the whole UK.

Works with **Claude**, **ChatGPT**, and **Gemini**.

Originally created for one student. Released so anyone studying Construction Management, Civil Engineering, Building Surveying, or related disciplines can use, customise, and improve it.

---

## What this does

- **First-run setup** captures your individual profile (name, university, year, target roles, locations, sectors, certifications)
- Generates ready-to-click search URLs for **8 UK student-relevant job sites** (Prospects, TARGETjobs, RateMyPlacement, LinkedIn, Indeed, Handshake, CareersinConstruction, your University Careers Service)
- Reads your CV and extracts a structured profile
- Scores each job 0–100 against your CV across 6 student-calibrated categories
- Tailors your CV using the STAR method — **without inventing experience** (uni projects, placements, part-time work, volunteering all count)
- Writes a STAR-based cover letter, addressing genuine gaps honestly
- Logs every application with **deadline tracking** (critical for grad schemes that close before stated deadline)
- Drafts follow-up emails (+10 days, +21 days — longer windows than mid-career)
- Tracks the **multi-stage assessment process** (Online Test → Video → Assessment Centre → Final)
- Generates **interview prep packs** including STAR question bank, technical questions calibrated for grad-level expectations, group exercise tips, and online test guidance

---

## Repository structure

```
student-construction-job-hunter/
├── README.md                   ← you are here
├── STUDENT_GUIDE.docx          ← human-readable walkthrough for first-time users
├── CONTRIBUTING.md             ← how classmates can improve the skill
├── LICENSE                     ← MIT — free to use, modify, share
├── .gitignore
│
├── claude/                     ← for Claude
│   ├── README.md
│   ├── SKILL.md                  (editable source)
│   └── student-construction-job-hunter.skill
│
├── chatgpt/                    ← for ChatGPT (Custom GPT)
│   ├── README.md
│   └── INSTRUCTIONS.md
│
├── gemini/                     ← for Gemini (Gem)
│   ├── README.md
│   └── INSTRUCTIONS.md
│
└── shared/                     ← reference files used by all three
    ├── job_sites.md
    ├── search_urls.md
    ├── scoring_rubric.md
    ├── sheet_schema.md
    ├── cv_template.md
    ├── cover_letter_template.md
    ├── followup_templates.md
    ├── interview_questions.md
    ├── uk_construction_keywords.md
    └── graduate_employers.md
```

---

## Quick install

### Claude
Download `claude/student-construction-job-hunter.skill` and upload via Settings → Skills → Upload. Done.

### ChatGPT
Create a Custom GPT, paste `chatgpt/INSTRUCTIONS.md` into the system instructions, upload all 10 files from `shared/` into the GPT's Knowledge.

### Gemini
Create a Gem, paste `gemini/INSTRUCTIONS.md` into the instructions, attach all files from `shared/`.

Each platform folder has its own `README.md` with detailed install steps.

---

## How to use it (after installing)

Open a fresh chat and say: **"I want to start using the job hunter."**

The skill will run its first-run setup — about 10 quick questions to capture your profile (university, year, target roles, location preferences, certifications). Save the profile JSON it gives you.

After that, attach your CV and say: **"Run Phase 0."**

Then drive it with natural language:
- *"Generate today's search URLs for placements."*
- *"Here's a JD I found on Prospects. Run Phase 2."*
- *"Tailor my CV for this one."*
- *"Got an interview at Mace next Tuesday. Help me prep."*

See `STUDENT_GUIDE.docx` for the full walkthrough with worked examples.

---

## Capability comparison

| Capability | Claude | ChatGPT | Gemini |
|---|---|---|---|
| Read uploaded CV (`.docx`, `.pdf`) | ✅ | ✅ | ✅ |
| Generate `.docx` for download | ✅ native | ✅ via Code Interpreter | ⚠️ usually returns text |
| Write to Google Sheets directly | ✅ if connector enabled | ✅ if connector / GPT Action | ✅ via Workspace |
| Web search (company research) | ✅ | ✅ | ✅ |
| Persistent memory between chats | ✅ if memory enabled | ✅ if memory enabled | ⚠️ limited |

The skill detects what it can and can't do, then adapts. If `.docx` generation isn't available, it outputs formatted text to copy into Word. If Sheets isn't connected, it outputs CSV rows for manual paste.

---

## Customising for yourself

The skill is built to be customised. Common things you might want to change:

- **Replace the placeholder STAR examples** in `shared/cv_template.md` and `shared/cover_letter_template.md` with your own real examples (clearly marked `[REPLACE WITH YOUR OWN]` in the template)
- **Add your university's careers portal URL** to `shared/search_urls.md` so it's pulled into search-URL generation
- **Add discipline-specific keywords** to `shared/uk_construction_keywords.md` if you're on a niche course
- **Adjust the scoring rubric** in `shared/scoring_rubric.md` if your priorities differ from the defaults

All reference files are plain markdown so you can edit them directly in the GitHub web UI or any text editor.

---

## Contributing improvements back

If you make something better — a new sample STAR example, an additional job site, a regional employer not on the list, a better cover letter for a specific tier 1 — please consider opening a pull request. See `CONTRIBUTING.md`.

---

## License

MIT — free to use, modify, share, and adapt. No warranty. See `LICENSE`.

---

## Honest limits

- The skill **cannot scrape job sites** for you — Prospects, LinkedIn, Indeed all block automation. It generates smart search URLs; you click and browse.
- It **cannot apply on your behalf** — each platform has its own apply flow. The skill prepares everything; you upload and submit.
- The fit score is **directional**, not gospel — a 60 you really want is more worth pursuing than an 80 you don't.
- It **doesn't know about every employer** — the graduate employers list is a non-exhaustive snapshot. Always check the employer's own careers page for current schemes.

Good luck with your search.
