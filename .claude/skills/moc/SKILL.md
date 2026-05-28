---
description: "Draft a Map of Content structure for a domain folder by clustering evergreen notes into thematic groups with connecting prose. Invoke explicitly with /moc — do not auto-trigger."
disable-model-invocation: true
---

Draft a Map of Content (MOC) structure for a domain folder.

Domain folder to map: $ARGUMENTS
(If not provided, ask which domain folder — e.g., `notes/40 Areas/3d-graphics`)

Steps:
1. Read all notes in the specified folder
2. Read the folder's `_README.md` for context
3. Identify evergreen notes (`status: evergreen`) — these are the nodes in the MOC
4. For notes that are still `status: fleeting` or `status: processing`, note them separately as "in progress"

Then produce:

**MOC structure draft**
Group the evergreen notes into 3-5 thematic clusters. For each cluster:
- A cluster title (e.g., "Clipping and Occlusion Techniques")
- 1-2 sentences describing how the notes in this cluster relate to each other
- A bulleted list of the notes that belong here with a one-line description of each

**Connecting prose**
Write 1-2 sentences for each cluster-to-cluster transition: how does understanding cluster A prepare you for cluster B?

**In-progress notes**
List the fleeting/processing notes and suggest which cluster they'll eventually belong to.

**Suggested MOC frontmatter:**
```yaml
type: moc
status: evergreen
domain: [domain]
tags: []
created: [today]
modified: [today]
```

Output this as a complete draft of `notes/50 Knowledge/mocs/moc-[domain].md` ready for me to review and save. Do NOT create the file — paste the full content here.
