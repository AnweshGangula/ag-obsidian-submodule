Generate a stand-up brief for a project.

Project folder: $ARGUMENTS
(If not provided, ask which project — look in `notes/30 Projects/active/`)

Steps:
1. Read all notes in the specified project folder, prioritizing `_project.md`
2. Look for the most recent updates (by `modified` date in frontmatter or file modification time)
3. Look for any linked notes in `notes/40 Areas/` that are referenced from this project

Produce a stand-up brief with these sections:

**Current phase**
One sentence on where the project is right now.

**Recent decisions**
2-3 bullets on key decisions made since last update (check the decision log in `_project.md`).

**Open questions**
What's unresolved? What needs a decision? (Look for TODO markers, question marks, or unresolved items.)

**Blockers**
Anything explicitly flagged as blocked or waiting on external input.

**Next actions**
3 concrete next steps, ordered by priority.

Keep the entire brief under 200 words. This is for a daily stand-up, not a status report.

Do NOT modify any files.
