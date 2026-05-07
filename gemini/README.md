# Gemini — Install Instructions

Gemini runs this skill via a **Gem** — Gemini's equivalent of a Custom GPT. Requires a paid tier (Google AI Pro / Google AI Ultra, or Google Workspace with Gemini).

## Quick install

1. Go to **gemini.google.com**
2. In the left sidebar, click **Gems** → **New Gem** (or **Gem manager** → **New**)
3. Fill in:
   - **Name:** `Student Construction Job Hunter`
   - **Instructions:** open `INSTRUCTIONS.md` in this folder, copy the entire contents, paste into the Instructions field
4. Under **Knowledge** (or **Files**, depending on Gemini version), upload **all 10 files** from the `../shared/` folder:
   - `job_sites.md`
   - `search_urls.md`
   - `scoring_rubric.md`
   - `sheet_schema.md`
   - `cv_template.md`
   - `cover_letter_template.md`
   - `followup_templates.md`
   - `interview_questions.md`
   - `uk_construction_keywords.md`
   - `graduate_employers.md`
5. Save the Gem

## If your Gemini tier doesn't support Gems

Use **one-shot setup** in a regular chat:

1. Open a new Gemini conversation
2. Paste the entire contents of `INSTRUCTIONS.md` as your first message
3. Attach all 10 files from `../shared/` to that same message
4. Attach your CV
5. Say: *"I want to start using the job hunter."*

You'll need to repeat this each new conversation, but it works on free Gemini tiers too.

## How to use

Open the Gem, say *"I want to start using the job hunter."* It runs first-run setup (~10 questions), then asks for your CV. After that, drive it naturally.

See `../STUDENT_GUIDE.docx` at the repo root for the full walkthrough.

## Notes specific to Gemini

- **`.docx` output is unreliable on Gemini.** Most tiers return formatted text rather than downloadable Word files. The skill is designed to handle this — when Gemini can't produce a `.docx`, it outputs the CV / cover letter as cleanly formatted text in a delimited block. Copy into Word and save as `.docx`.
- **Google Sheets is Gemini's strength** — if you're on a Workspace plan, Gemini can read and write to your application log sheet directly. Just provide the URL when asked.
- **Memory between chats is limited.** Save the JSON profile from first-run setup to your Drive or a note, and re-attach at the start of each new session.
- **Web search works well** for company research during interview prep.

## Updating the Gem

When you edit any file in `../shared/`:

1. Open the Gem in edit mode
2. Under Knowledge, remove the old file and upload the updated one
3. If you edited `INSTRUCTIONS.md`, replace the contents in the Instructions field
4. Save

Changes apply immediately to new conversations with the Gem.
