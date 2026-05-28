---
description: "Manage project lifecycle: scaffold new projects, get stand-up briefs, close with retrospective, or update status. Use when the user describes starting a project, asks for a project summary, wants to close/archive a project, or asks to change a project's status."
---

Manage a project in `notes/30 Projects/`.

Usage: `/project [action] [project-name-or-path]`

If invoked with no arguments or just a project name with no action: list all active and on-hold projects (read `notes/30 Projects/` and find all notes with `type: project`), then ask which action to take.

---

## Action: `new`

Trigger: `/project new [name]` or when the user describes wanting to start a project.

Steps:
1. If name/description not provided, ask for: (1) project name, (2) type (work / personal / learning / life), (3) primary domain (or none), (4) one paragraph describing the goal and what "done" looks like
2. Read `notes/00 _System/templates/project-template.md` for the structure
3. Determine a URL-friendly slug for the folder name (e.g., "Learn 3DGS Pipeline" → `learn-3dgs-pipeline`)
4. Fill all template sections:
   - Brief: synthesise from the description
   - End State: distil to one testable sentence
   - Phases: suggest 2-3 logical phases based on the goal
   - Frontmatter: type, project-type, domain, dates (use today's date)
5. Output the complete `_project.md` draft for review

Then ask: **"Create `notes/30 Projects/[slug]/_project.md`?"**
On confirmation: create the folder and write the file.

---

## Action: `brief`

Trigger: `/project brief [project-path]`

Steps:
1. If path not provided, list active projects and ask which one
2. Read all notes in the specified project folder, prioritising `_project.md`
3. Check `modified` date — note how long since last update

Produce a stand-up brief:

**Current phase** — one sentence on where the project is now.
**Recent decisions** — 2-3 bullets from the Decision Log (most recent entries).
**Open questions** — unresolved items, TODO markers, question marks in notes.
**Blockers** — anything flagged as blocked or waiting on external input.
**Next actions** — 3 concrete next steps, ordered by priority.

Keep the entire output under 200 words. This is a stand-up, not a status report.

Do NOT modify any files.

---

## Action: `close`

Trigger: `/project close [project-path]`

Steps:
1. If path not provided, list active projects and ask which one
2. Read `_project.md` fully
3. Summarise: completed phases, key decisions made, linked domain notes generated

Then ask 3 retrospective questions:
1. "What worked well in this project?"
2. "What didn't work or what would you do differently?"
3. "What's the most important thing to carry forward — either as a domain note or a principle?"

(If `_project.md` is already rich enough to infer answers, draft responses and ask for corrections rather than asking from scratch.)

With the answers:
4. Fill the Retrospective section of `_project.md`
5. Update frontmatter: `status: completed`, `modified: [today]`
6. Show the full diff → ask for confirmation before writing

After write confirmation:
7. Show the move: `notes/30 Projects/[name]/` → `notes/90 Archive/completed-projects/[name]/`
8. Ask for confirmation before moving

Do NOT move files without explicit confirmation.

---

## Action: `status`

Trigger: `/project status [project-path]`

Steps:
1. If path not provided, list active projects and ask which one
2. Read `_project.md`, show current status
3. Ask for new status: `fleeting | active | on-hold | completed`
   - If `on-hold`: ask for a one-line reason to note in the Brief section
   - If `completed`: recommend running `/project close` instead for a proper retrospective
4. Update frontmatter `status` and `modified`
5. Show diff → ask for confirmation before writing

---

## Project status reference

| Status | Meaning |
|---|---|
| `fleeting` | Scaffolded but not yet actively worked on |
| `active` | Currently in progress |
| `on-hold` | Paused — reason noted in Brief |
| `completed` | Done, retrospective written |
| `archived` | Moved to `90 Archive/` (set by `close` action) |

Valid `project-type` values: `work` | `personal` | `learning` | `life`

Template location: `notes/00 _System/templates/project-template.md`
