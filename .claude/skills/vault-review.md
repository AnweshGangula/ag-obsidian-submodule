---
description: "Run the complete Sunday weekly vault review: inbox audit, stale fleeting notes, promotion candidates from daily notes, and domain health summary. Invoke explicitly with /vault-review — do not auto-trigger."
disable-model-invocation: true
---

Run a complete weekly vault review. This is the Sunday 1-hour ritual command.

Arguments (optional): $ARGUMENTS — pass a date range like `2026-05-11 to 2026-05-18`, otherwise defaults to the last 7 days.

This command runs four sequential checks and outputs a complete review brief.

---

## Step 1: Inbox Audit

Read all files in `notes/10 Inbox/`.
For each file, output:
- Filename and first 50 words
- Suggested destination (which PARA folder and sub-folder)
- Suggested action: file it, delete it, or needs more reading

---

## Step 2: Stale Fleeting Notes

Search `notes/40 Areas/` and `notes/50 Knowledge/` for notes with `status: fleeting` that have not been modified in more than 14 days.
List them with: path, domain, days since last modified.
For each one: recommend "promote", "delete", or "defer" with a one-line reason.

---

## Step 3: Promotion Candidates from Daily Notes

Read all daily notes in `notes/20 Journal/daily/` modified in the last 7 days.
Find all bullet points prefixed with `$`.
Group them by technical topic.
For each group: recommend a target in `notes/40 Areas/[domain]/` (existing note or new concept doc).
Output as a promotion plan — enough detail to execute without re-reading the daily notes.

---

## Step 4: Domain Health Summary

For each domain in `notes/40 Areas/`:
- Count notes by status (fleeting / processing / evergreen)
- Flag any domain with 0 evergreen notes and 5+ fleeting notes (backlog risk)
- Flag any domain with 6+ evergreen notes and no MOC yet (MOC opportunity)

---

## Output format

Section headers as above, results in bullet lists. Target total length: 400-600 words.
This is actionable output — every item should have a clear next action.

Do NOT modify any files. This is a read-only review.
