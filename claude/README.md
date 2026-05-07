# Claude — Install Instructions

## Quick install

1. Download `student-construction-job-hunter.skill` from this folder
2. Open Claude → Settings → Skills (or Capabilities → Skills depending on your tier)
3. Click **Upload skill** and select the `.skill` file
4. Done. Claude will trigger automatically when you mention construction job hunting, paste a JD, ask to tailor a CV, etc.

The `.skill` file is a zip archive with a different extension. Claude unpacks it server-side on upload — you don't need to extract anything yourself.

## What's inside the .skill file

```
student-construction-job-hunter/
├── SKILL.md                   ← main instructions (with YAML frontmatter)
└── references/
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

## How to use

Once installed, just talk naturally. Useful starter prompts:

- *"I want to start using the job hunter."* → triggers first-run setup
- *"Run Phase 0."* (after attaching your CV)
- *"Generate today's search URLs for placements in Manchester and Leeds."*
- *"Here's a JD I found on Prospects. Run Phase 2, then Phase 3 if the score is 60+."*
- *"Got an interview at Mace next Tuesday. Help me prep."*

See `../STUDENT_GUIDE.docx` at the repo root for the full walkthrough.

## Rebuilding the .skill file after edits

If you edit `SKILL.md` in this folder or any reference file in `../shared/`, you'll need to repackage the `.skill` file before uploading the updated version to Claude.

### Mac/Linux:

```bash
# From the repo root
mkdir -p /tmp/build/student-construction-job-hunter
cp claude/SKILL.md /tmp/build/student-construction-job-hunter/
cp -r shared /tmp/build/student-construction-job-hunter/references

cd /tmp/build
zip -r student-construction-job-hunter.skill student-construction-job-hunter/

mv student-construction-job-hunter.skill ~/path/to/your/repo/claude/
```

### Windows (PowerShell):

```powershell
$build = "$env:TEMP\build\student-construction-job-hunter"
New-Item -Path $build -ItemType Directory -Force
Copy-Item claude\SKILL.md $build\
Copy-Item -Recurse shared $build\references

Compress-Archive -Path "$env:TEMP\build\student-construction-job-hunter" `
                 -DestinationPath claude\student-construction-job-hunter.zip -Force
Rename-Item claude\student-construction-job-hunter.zip claude\student-construction-job-hunter.skill -Force
```

After rebuilding, re-upload the new `.skill` file via Settings → Skills.

## Notes

- Claude with the Google Drive / Sheets connector enabled will write your application log directly to a sheet
- Claude can produce tailored CVs and cover letters as `.docx` files for download natively
- If you change CV versions, run Phase 0 again with the new CV to refresh the profile
- First-run setup only runs once per skill installation; if you want to re-run it, just say "re-run the first-run setup" or "update my profile"
