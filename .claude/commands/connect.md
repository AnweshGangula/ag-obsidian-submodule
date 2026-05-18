Find unlinked related notes for a given note.

Note to find connections for: $ARGUMENTS
(If not provided, ask which note to analyze)

Steps:
1. Read the specified note fully
2. Extract the key concepts, technologies, and patterns it covers
3. Search across `notes/40 Areas/`, `notes/50 Knowledge/`, and `notes/30 Projects/` for notes that:
   - Cover the same technology or concept from a different angle
   - Are prerequisite knowledge for the specified note
   - Build on the concepts in the specified note
   - Share tags or domain with this note
4. Check the existing `[[wikilinks]]` in the note — exclude any already-linked notes from suggestions

For each candidate connection found, output:
- The path to the related note
- One sentence explaining WHY they should be linked (the conceptual relationship)
- Which direction the link should go: `[this note] → [that note]`, `[that note] → [this note]`, or bidirectional

Organize suggestions by relationship strength: "Strong connections" (directly related), "Useful context" (background/prerequisite), "See also" (tangentially related).

Limit to the top 10 most useful connections. Quality over quantity.

Do NOT modify any files. Output the connection suggestions here for my review.
