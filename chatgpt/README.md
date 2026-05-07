# ChatGPT — Install Instructions

ChatGPT runs this skill via a **Custom GPT** (requires ChatGPT Plus, Team, or Enterprise).

## Quick install

1. Go to **chatgpt.com** → **Explore GPTs** → **Create** (top-right)
2. Click the **Configure** tab (skip the conversational builder)
3. Fill in:
   - **Name:** `Student Construction Job Hunter`
   - **Description:** `For UK construction students. Finds graduate roles and placements, tailors CVs using STAR (no fabrication), tracks applications, prepares for grad scheme interviews.`
   - **Instructions:** open `INSTRUCTIONS.md` in this folder, copy the entire contents, paste into the Instructions field
4. Under **Knowledge**, click **Upload files** and upload **all 10 files** from the `../shared/` folder:
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
5. Under **Capabilities**, enable:
   - ✅ **Web Browsing** (for company research during interview prep)
   - ✅ **Code Interpreter & Data Analysis** (lets it generate `.docx` files for download)
   - ❌ DALL·E (not needed)
6. Click **Create** → **Save** → choose **Only me** for visibility (recommended for personal use)

## Conversation starters (optional)

In the Configure tab, add these as suggested prompts:

- `I want to start using the job hunter — run first-run setup.`
- `Run Phase 0 — my CV is attached.`
- `Generate today's search URLs for grad schemes.`
- `Here's a JD. Run Phase 2 and 3 if the score is 60+.`
- `Got an interview — help me prep.`

## How to use

Open the GPT and say *"I want to start using the job hunter."* The GPT will walk you through first-run setup (~10 questions), then ask you to attach your CV. After that, drive it with natural language.

See `../STUDENT_GUIDE.docx` at the repo root for the full walkthrough.

## Notes

- ChatGPT generates `.docx` via Code Interpreter — tailored CVs and cover letters come out as downloadable Word files
- For Google Sheets: connect Google in ChatGPT settings (Plus/Team supports this), then it can read/write your application log directly. If not connected, the GPT outputs CSV rows for manual paste.
- If ChatGPT memory is enabled, your profile persists between chats. If not, save the JSON from first-run setup and re-paste at session start.

## Updating the GPT

When you edit any file in `../shared/`:

1. Open your Custom GPT in **Edit GPT** mode
2. Under Knowledge, **delete the old file** and **upload the updated one**
3. If you edited `INSTRUCTIONS.md`, replace the contents in the Instructions field
4. Click **Update**

Changes apply immediately to new conversations.
