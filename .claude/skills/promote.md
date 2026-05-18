---
description: "Process $ promotion-candidate bullets from a daily journal note into concept note drafts with Prose Tax paragraphs and suggested frontmatter. Use when the user pastes daily note content containing $ bullets or asks to process/promote captures from a daily note."
---

Process the promotion candidates from a daily note.

Read the file at: $ARGUMENTS
(If no path provided, ask which daily note to process — look in `notes/20 Journal/daily/`)

Find all bullet points prefixed with `$`. For each one:

1. **Determine the best target location:**
   - Which sub-folder of `notes/40 Areas/` does this belong to?
   - Which existing note in that folder should it be added to, OR should a new concept note be created?
   - A new note is warranted when: this bullet introduces a distinct concept not yet covered, OR there are 3+ related `$` bullets across this week's daily notes that cluster around the same topic.

2. **Draft a Prose Tax paragraph:**
   - Write a synthesis paragraph (2-4 sentences) that answers: "What does this mean for how I build things?"
   - Do NOT summarize — state an original claim or implication.
   - This must be original synthesis, not a rephrasing of the bullet.

3. **Suggest frontmatter:**
   - type: note
   - status: processing (it becomes `evergreen` after you accept the Prose Tax)
   - domain: [correct domain]
   - tags: [2-4 specific tags from the vault's tag taxonomy]

**Output format:** A structured promotion plan — one section per cluster/bullet. Show me the target, the drafted Prose Tax paragraph, and the frontmatter. Do NOT write or modify any files. I will copy-paste the accepted content myself.

Reference `notes/00 _System/claude/writing-guide.md` for prose conventions.
