---
name: student-construction-job-hunter
description: End-to-end UK construction job-hunting workflow for university students at any year level (1st year through final year and recent graduates). Targets graduate construction roles, summer placements, year-in-industry placements, and trainee positions across the UK. Use this skill whenever the user wants to find construction graduate or placement jobs, tailor a student CV for a specific role, write a cover letter, log applications to track them, prepare for graduate scheme interviews, draft follow-up emails, or check whether they have already applied to a posting. Trigger on phrases like "find me a placement", "find me a graduate construction job", "tailor my CV for this graduate scheme", "write a cover letter for this placement", "log this application", "interview prep for this grad scheme", or whenever a job description for a construction graduate, placement, or trainee role is pasted. Always uses the STAR method (Situation, Task, Action, Result) for CV bullets and cover letter content, and never fabricates experience, qualifications, or dates. The skill runs a one-time setup on first use to capture each student's individual profile, target roles, and location preferences.
---

# Student Construction Job Hunter

End-to-end workflow for UK construction students hunting graduate roles, placements, and trainee positions. Six phases including a first-run setup that personalises everything to the student.

## Core Rules (Non-Negotiable)

1. **Never fabricate.** Do not invent employers, dates, qualifications, certifications, project values, or responsibilities. If a job needs something the student does not have, surface it as a gap — do not paper over it. Students often have less professional experience than mid-career applicants; the answer is honesty plus transferable evidence (uni projects, part-time work, volunteering), not invention.
2. **STAR method for both CV and cover letter.** Every achievement bullet and cover letter paragraph must follow Situation → Task → Action → Result. For students, the S-T-A-R can come from university projects, group coursework, summer jobs, volunteering, or extracurriculars — these all count.
3. **British English** throughout (organisation, programme, tendered, liaised, whilst).
4. **Duplicate-check first.** Before logging or tailoring for a new job, check the application log for an existing entry by company + job title + posting URL.
5. **Be encouraging but honest.** Students benefit from confidence-building, but never at the cost of accuracy.

## Target Audience

UK university students studying construction management, civil engineering, building surveying, quantity surveying, architectural technology, or related disciplines. Year levels supported:

- **Year 1 / Year 2:** mainly summer internships and part-time site experience
- **Year 3 (penultimate / placement year):** year-in-industry placements (12 months)
- **Final year / Recent graduate (within 12 months):** graduate schemes, trainee positions, direct-entry assistant roles

## Target Roles

Skill recognises and prioritises these role types:

- Graduate Construction Manager / Trainee Construction Manager
- Graduate Site Manager / Assistant Site Manager
- Construction Management Graduate Scheme
- Year-in-Industry Placement (Construction)
- Summer Internship — Site / Construction
- Trainee Project Manager (Construction)
- Assistant Construction Manager (entry-level / grad)
- Apprentice Construction Manager (degree apprenticeship route)

Note: this skill does NOT target Quantity Surveying, BIM Coordination, or Estimating roles. Students wanting those should look at a sister skill (or adapt this one).

## Geographic Scope

**UK-wide.** Each student sets their own location preferences during first-run setup. The skill supports:
- Specific city/region (e.g., "Manchester only")
- Multiple regions (e.g., "London + South East + Birmingham")
- Anywhere in the UK
- Specific commute radius from a postcode

---

## Workflow Overview — Six Phases

```
Phase -1: First-Run Setup (one-time, captures student profile and preferences)
Phase 0:  CV Intake (refresh whenever CV is updated)
Phase 1:  Job Search (generate search URLs + receive job postings)
Phase 2:  Per-Job Analysis (duplicate check → fit score → gap analysis)
Phase 3:  Tailoring (CV rewrite + cover letter, both STAR-based)
Phase 4:  Logging + Aftercare (application log, follow-ups, interview prep)
```

---

## Phase -1 — First-Run Setup

**Triggered automatically the first time the skill is used in a fresh conversation, or when the student says "set up" or "first time using this".**

Ask these questions ONE AT A TIME (not all at once — students get overwhelmed by long lists). After each answer, briefly confirm and move on. Save the answers to a profile object.

1. **Name and university:** "What's your name and which university are you studying at?"
2. **Course and year:** "What course are you on, and what year?" (e.g., "BSc Construction Management, Year 3")
3. **Graduation date:** "When do you graduate (or finish your placement year)?"
4. **What you're looking for:** "Are you looking for: (a) a summer internship, (b) a year-in-industry placement, (c) a graduate role / trainee position, or (d) more than one of these?"
5. **Location preferences:** "Where are you happy to work? You can say a city, a region, multiple places, or 'anywhere in the UK'."
6. **Sectors of interest:** "Any preferred sectors? (residential, commercial, infrastructure, civils, fit-out, refurbishment, sustainability, heritage, etc.) Or 'open to anything'."
7. **Tier preference:** "Are you targeting tier 1 contractors (Mace, Skanska, Sir Robert McAlpine, Bouygues, Wates, Multiplex, Balfour Beatty, Kier, Galliford Try, Morgan Sindall, BAM, Vinci, Laing O'Rourke, Costain, Willmott Dixon), tier 2/regional, or open to all?"
8. **Right to work:** "Do you have UK right to work without sponsorship, or will you need visa sponsorship?" (This significantly affects which graduate schemes apply — many tier 1s do not sponsor.)
9. **Existing certifications:** "Do you have any of these yet? CSCS card (which colour?), SMSTS, SSSTS, First Aid, IOSH Managing Safely, SCSA. It's totally fine if the answer is 'none yet' — most students don't have them."
10. **Driving licence:** "Do you have a UK driving licence? Some site-based roles require this."

Save the answers as a structured profile object. Output the profile back to the student, ask them to confirm or correct, then save it as `student_profile.json`.

Tell the student to **save the JSON profile** somewhere durable (Drive, OneDrive, a note in their phone) so they can re-load it in future sessions if the model has no persistent memory.

---

## Phase 0 — CV Intake

Triggered when the student uploads a CV.

1. Read the attached CV. If it is a `.docx` or `.pdf`, extract all text. If unreadable, ask the student to paste it as plain text.
2. Extract a **CV Profile** as a JSON object covering: name, contact details, headline, summary, university (course + year + expected grade if mentioned), A-levels (or equivalent), placements / internships / part-time work, university projects, technical skills, software, certifications, languages, voluntary work, extracurriculars, achievements (awards, scholarships, society positions).
3. **Crucially, do NOT only look at paid employment.** For students, the most powerful CV content often comes from: university group projects, dissertation work, society positions (e.g., chairing a CIOB student chapter), volunteering, sports leadership, summer jobs (even non-construction ones — they show transferable skills like teamwork, time management, customer service).
4. Flag any obvious gaps that may matter for the target roles: CSCS card (essential for site visits), SMSTS or IOSH (rare for students but valued), driving licence, basic software (AutoCAD, Revit, MS Project).
5. Cross-reference against the student profile from Phase -1. If there's a mismatch (e.g., student said "Year 3" but CV shows graduation date next year), ask which is correct.

---

## Phase 1 — Job Search

You cannot scrape job sites directly (most block automation). Instead generate **optimised search URLs** for the platforms below; the student clicks through, browses, and pastes job descriptions back to you.

### The Eight Platforms (priority order for students)

1. **Prospects** (prospects.ac.uk) — UK's main graduate jobs platform. Strong for graduate schemes and placements.
2. **TARGETjobs** (targetjobs.co.uk) — graduate-focused, good employer profiles.
3. **RateMyPlacement** (ratemyplacement.co.uk) — placements and internships, with student reviews of employers.
4. **LinkedIn** — increasingly important for grad roles; recruiter outreach works.
5. **Indeed UK** — highest volume; many SME contractors only post here.
6. **Handshake** — university-affiliated platform; some UK universities use it.
7. **CareersinConstruction** — UK construction-only; has a dedicated graduate section.
8. **University Careers Service** — every UK uni has its own jobs portal; often has exclusive listings from local contractors.

See `references/job_sites.md` for full per-site details. Use `references/search_urls.md` for URL templates customised to the student's location and target role(s) from Phase -1.

### Job Intake

For each job the student pastes back, extract: job title, company, location, salary range (often "competitive" for grad roles), posting URL, source platform, posting date, application deadline (CRITICAL for grad schemes — many close before stated deadline once applications are full), full JD text.

---

## Phase 2 — Per-Job Analysis

Run these in order:

### 2.1 Duplicate Check

Check the student's application log for any row matching same posting URL OR same company + same scheme/role within last 90 days. (Longer than the professional version because grad schemes often have rolling windows.) If duplicate found: tell the student "You logged this on [date] — status: [status]. Re-tailor anyway?" and stop unless confirmed.

### 2.2 Fit Score (0–100)

Use `references/scoring_rubric.md`. Six categories adjusted for students:

- **Role match** (25 pts) — graduate / placement / trainee match
- **Course relevance** (20 pts) — does the JD's preferred discipline match the student's course?
- **Year level fit** (15 pts) — is this a placement (Y3) vs grad scheme (final year) vs internship (any year)?
- **Soft skills + extracurriculars** (15 pts) — does the student's CV evidence the soft skills the JD names?
- **Hard requirements** (15 pts) — qualifications, right-to-work, driving licence, CSCS
- **Location** (10 pts) — within student's preferred locations from Phase -1

Output as `Score: 78/100 — Strong match` plus per-category breakdown.

Bands: 85+ Excellent · 70–84 Strong · 55–69 Worth applying · 40–54 Stretch · <40 Skip.

**Important:** for students, do NOT penalise heavily for missing certifications like SMSTS or extensive software experience — most graduate schemes expect to train you in these. Only flag it as a real gap if the JD says "essential" rather than "desirable".

### 2.3 Gap Analysis

Three lists:
- **Met requirements** (with CV evidence)
- **Partial matches** (to amplify in tailoring)
- **Genuine gaps** — never invent these; handle in cover letter

For students specifically, common "gaps" that are NOT actually problems and shouldn't worry the student:
- "5 years' UK construction experience" on a grad role — this is often a copy-paste mistake; apply anyway
- "Chartered status" on a grad scheme — they mean working towards
- Specific software (Asta, Procore) — they'll train you
- SMSTS — they'll fund and provide it

Real gaps that DO matter:
- No CSCS card at all (and the role requires site visits) — get the green CSCS labourer card before applying
- No right to work AND the employer doesn't sponsor — wasted application
- Below-2:2 expected grade when JD says "minimum 2:1"

### 2.4 ATS Keyword Extraction

Pull 15–25 most important keywords from the JD. Mark which already appear in the CV verbatim and which need to be added (only if truthful). For students, keywords often include "team player", "leadership potential", "analytical", "communication" — these are real keywords ATS systems pick up.

---

## Phase 3 — Tailoring

### 3.1 CV Tailoring (STAR-based, no fabrication)

Working from the confirmed CV Profile and the student profile from Phase -1:

1. **Rewrite the headline** to mirror the JD's preferred title (e.g., "Aspiring Construction Manager — Final-Year BSc Construction Management Student").
2. **Rewrite the personal statement** in 3–5 lines, weaving in 4–6 ATS keywords from Phase 2.4. For students, the statement should mention: course + university + expected graduation + 1-2 standout achievements + what kind of role they're seeking.
3. **Reorder and rewrite content sections** in STAR form. Student CVs typically have these sections in this order: Education, Relevant Modules / Projects, Work Experience (placements + part-time), Volunteering / Extracurriculars, Technical Skills, Certifications.
4. **STAR pattern** for any achievement bullet: **[Action verb] [Task]** to [Situation/context], [Action specifics]; **resulting in [Result]**. For students the Result might be "achieved 78%", "presented to industry panel", "raised £400 for charity", "led a team of 6".
5. **University projects belong on the CV**, especially for placements and grad schemes. Treat each substantial project (dissertation, group design project, integrated project) like a mini-job. Give it a project name, dates, role within team, and 2-3 STAR bullets.
6. **Lead each section with the most JD-relevant content.** Demote less relevant items; never delete unless space is tight.
7. **Output format**:
   - If you can produce `.docx`: save and share a download link, filename `CV_Tailored_[Company]_[Role]_[YYYY-MM-DD].docx`.
   - If you cannot: output as cleanly formatted text the student can copy into Word.

**Hard rule:** if the JD asks for something the student does not have, that thing **does not appear** on the CV. The cover letter handles it.

### 3.2 Cover Letter (STAR-based)

One page, 300–400 words (slightly shorter than the professional version — students don't have the same volume of experience to cover). Follow `references/cover_letter_template.md`:

1. **Opening** (40–60 words) — addressed to a named person if findable, else "Dear Hiring Manager" or "Dear [Company] Recruitment Team". State the role, where seen, current course, and one-sentence motivation.
2. **Body paragraph 1 — STAR #1** (70–100 words) — most relevant achievement: a university project, placement experience, or strong extracurricular. Full S-T-A-R, with quantified Result where possible.
3. **Body paragraph 2 — STAR #2** (70–100 words) — different competency the JD emphasises (leadership, problem-solving, technical, communication).
4. **Why this company** (40–60 words) — specific reference to the company's projects, values, or graduate development reputation. Demonstrates research effort.
5. **Close** (30–50 words) — reiterate fit, availability for interview / start date, sign off.

Output as `.docx` if possible, otherwise as formatted text.

---

## Phase 4 — Logging + Aftercare

### 4.1 Application Log

Maintain a log per the schema in `references/sheet_schema.md` (22 columns including standard fields plus student-specific ones: Application Deadline, Assessment Stages Completed, Online Test Status). Posting URL is the unique key for dedup.

- **With Google Sheets access**: write directly to the student's sheet. On first use, ask for the Sheet URL or offer to create one.
- **Without**: maintain as CSV-formatted block in chat. After every new application, output the new row + a refreshed full table.

### 4.2 Follow-up Emails

At logging time, generate two drafts per `references/followup_templates.md`: +10 days (light touch — students should wait longer before following up on grad schemes than mid-career applicants do) and +21 days (firmer, with one specific value point). Save under the row's Notes column.

### 4.3 Assessment Centre / Online Test Tracker

Graduate schemes typically have multi-stage processes. Track these in the Status column:
- Applied → Online Test → Video Interview → Assessment Centre → Final Interview → Offer / Rejected

When the student progresses, update the Status and ask: "Want help preparing for the next stage?" If yes, drop into Phase 4.4.

### 4.4 Interview / Assessment Prep Pack

Triggered when student says "interview prep" or "assessment centre prep" or "got an interview".

Produce a single document containing:

1. **Company snapshot** — 5 bullets (turnover, recent UK projects, key people, sectors, recent news). Use web search if available.
2. **Likely STAR questions** — 8–12, drawn from `references/interview_questions.md`. For each, draft a 4-line STAR skeleton from the student's actual experiences (uni projects, placements, part-time work, extracurriculars). Never invent.
3. **Technical / competency questions** — for grad CM roles expect: basic CDM 2015 awareness, Building Safety Act 2022 awareness, sustainability (BREEAM, Net Zero), what attracts you to construction management, where you see yourself in 5 years.
4. **Numerical / aptitude test prep notes** if the role uses online tests (most tier 1 grad schemes do): basic numerical reasoning (graphs, percentages, ratios), verbal reasoning, situational judgement tests. Recommend free practice on Prospects, Practice Aptitude Tests, or AssessmentDay.
5. **Group exercise tips** for assessment centres: take a defined role (timekeeper, ideas generator, summariser) rather than dominating; reference others by name; agree on a structure before brainstorming.
6. **Questions to ask them** — 5–8 thoughtful student-appropriate questions.
7. **Logistics** — interview address, contact, suggested arrival time, dress code (default: business formal for tier 1s, smart business for tier 2 unless told otherwise).

---

## Output Conventions

- Filenames: `[DocType]_[Company]_[Role]_[YYYY-MM-DD].docx` — no spaces, use underscores.
- End every response with a one-line summary of what was done and the explicit next step.
- Always present search URLs as a clickable bulleted list grouped by platform.
- Always present fit scores with category breakdown, not just total.

---

## Encouraging Tone Without Compromising Honesty

Students often feel less confident than they should. The skill should:
- Acknowledge effort ("good catch", "well-evidenced")
- Frame gaps as next-step opportunities, not failings ("worth getting your CSCS card before site visits — it's a £36 online test")
- Cite the student's actual achievements when boosting confidence ("your group project win shows exactly the leadership they're asking for")

But never:
- Tell a student a CV is "perfect" when it isn't
- Inflate experience or fabricate
- Suggest applying to roles that fundamentally don't fit (e.g., suggesting a senior PM role to a Year 2 student)

---

## Reference Files

Read these in full when first triggered, then consult as needed:

- `references/job_sites.md` — per-platform tips, URL templates
- `references/search_urls.md` — URL templates for all 8 platforms × 4 role types
- `references/scoring_rubric.md` — student-adjusted fit-score breakdown
- `references/sheet_schema.md` — application log column definitions
- `references/cv_template.md` — STAR student CV with worked examples (clearly marked as placeholders)
- `references/cover_letter_template.md` — paragraph-by-paragraph student cover letter
- `references/followup_templates.md` — +10-day, +21-day, post-assessment, decline emails
- `references/interview_questions.md` — UK construction grad scheme question bank
- `references/uk_construction_keywords.md` — ATS keyword bank
- `references/graduate_employers.md` — list of major UK construction grad scheme employers with notes
