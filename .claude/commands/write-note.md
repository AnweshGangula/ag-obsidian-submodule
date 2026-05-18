Draft a new concept note from raw bullet captures.

Input: $ARGUMENTS
Format: `[topic-name] | [bullet1] | [bullet2] | [bullet3] ...`
Or paste multi-line bullets directly after the command.

If no input is provided, ask for: (1) the topic/title, (2) the raw bullet points or notes to synthesize.

Steps:
1. Read `notes/00 _System/claude/writing-guide.md` for prose conventions
2. Determine the correct domain from the topic content
3. Read the domain context file at `notes/00 _System/claude/domains/[domain].md` if it exists
4. Search `notes/40 Areas/[domain]/` for any existing note this content should be added to (rather than creating a new file)

Then produce a complete concept note:

**Frontmatter** (complete, ready to paste):
```yaml
---
type: note
status: processing
domain: [determined domain]
tags: [2-4 specific tags from vault taxonomy]
created: [today's date]
modified: [today's date]
---
```

**Title** — descriptive, kebab-case-compatible (e.g., `webgl-clipping-bvh-vs-stencil`)

**Body** — structured as:
1. Opening claim (1 sentence): the main insight or concept
2. Context (1-2 paragraphs): what this is, why it matters, technical details
3. Code example (if applicable): minimal working example with explanation
4. **Prose Tax paragraph**: synthesis answering "What does this mean for how I build things?" — this is the most important section. Original claim, not a summary.
5. Links: `[[wikilinks]]` to related notes I should connect this to (suggest 2-3)

Output the complete note content ready to save. Suggest the filename.
Do NOT create the file — I will save it myself after review.

This note starts at `status: processing`. I will change it to `status: evergreen` after I verify the Prose Tax paragraph meets the bar.
