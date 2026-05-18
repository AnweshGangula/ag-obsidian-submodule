---
description: "Run the next step of the AG Second Brain v2 vault migration with step-by-step approval. Invoke explicitly with /migrate — do not auto-trigger."
disable-model-invocation: true
---

Run the next step of the AG Second Brain v2 vault migration.

Optional argument: $ARGUMENTS — pass a week number (2, 3, or 4) to force a specific week. If omitted, auto-detect from the migration status table.

---

## Phase 1: Detect current migration state

Read `notes/40 Areas/pkm/vault-architecture-v2.md`.
Find the Migration Status table. Identify the **first week still marked ⏳ Pending**.
Report: "Currently on Week N — [scope description]"

If $ARGUMENTS is a number (2, 3, or 4), use that week instead of auto-detected.
If all weeks are ✅ Complete, congratulate and stop.

---

## Phase 2: Analyze — build the move plan

Before touching anything, survey the vault and produce a concrete, file-level plan.

### Week 2 analysis
1. List all files and sub-folders inside `notes/10-19 Calendar/` (recursively)
2. For each file, determine the destination inside `notes/20 Journal/`:
   - Daily notes → `notes/20 Journal/daily/2026/` (or matching year sub-folder)
   - Weekly notes → `notes/20 Journal/weekly/`
   - Periodic/monthly notes → `notes/20 Journal/periodic/`
   - Anything else → flag it for manual review
3. Scan all `.md` files in `notes/` for Dataview `FROM` lines referencing `10-19` or `Calendar` paths — list each file and the affected query line
4. Note (do NOT execute): Periodic Notes plugin config will need its paths updated to `notes/20 Journal/` — this requires a manual change inside Obsidian settings after the file moves are done

### Week 3 analysis
1. List all sub-folders inside `notes/30-39 Areas/`
2. For each sub-folder, propose a destination domain in `notes/40 Areas/`:
   - Map based on folder names and the domain list in CLAUDE.md
   - Flag any sub-folder that doesn't cleanly map to a single domain
3. For each sub-folder, list its files and note the destination path
4. Scan all `.md` files for wikilinks `[[...]]` and Dataview `FROM` lines referencing `30-39` paths — list them grouped by source file
5. ⚠️ Week 3 is the highest-risk week. Flag any ambiguous mappings clearly before proceeding.

### Week 4 analysis
1. Locate the current Projects folder (likely `notes/40-49 Projects/` or similar) — list files, map to `notes/30 Projects/`
2. Locate the current Career folder (likely inside `notes/30-39 Areas/` or `notes/60-69 Career/`) — map to `notes/40 Areas/career/`
3. Locate the current AI Agents folder (likely `notes/50-59 AI & Agents/`) — map to `notes/60 Agents/`
4. Find all old numbered top-level folders still present — these are candidates for deletion after moves
5. Find all notes in `notes/40 Areas/` and `notes/50 Knowledge/` that are missing a `status` frontmatter field — list them (these need manual frontmatter addition)

---

## Phase 3: Present plan and get approval

Output the complete move plan as a structured list:
```
WEEK N MOVE PLAN
================
[N] files to move
[N] Dataview queries to update after move
[N] items flagged for manual review

Moves:
  notes/old-path/file.md → notes/new-path/file.md
  ...

Dataview queries needing update after move:
  notes/some-note.md (line 42): FROM "notes/10-19 Calendar"
  ...

Manual actions (cannot be automated):
  - [ ] Update Periodic Notes plugin path in Obsidian settings
  ...
```

Then display this warning:

> **⚠️ Link-update caveat:** Moving files via Claude Code bypasses Obsidian's automatic link-update mechanism. Wikilinks pointing to moved files may break. This command will run a link-check after every move batch and report any broken references. Alternatively, you can do moves from inside Obsidian (right-click → Move file to folder) which updates links automatically — then just tell me to run the link-check step only.

Ask: **"Proceed with these moves? (yes / no / obsidian-only)"**
- `yes` → proceed to Phase 4
- `no` → stop, output the plan as a checklist the user can execute manually
- `obsidian-only` → skip file moves, go straight to Phase 5 (link-check) after user has done moves in Obsidian

---

## Phase 4: Execute moves

Move files in batches. For Week 3, move **one sub-folder at a time** — confirm after each before proceeding to the next.

After each batch:
- Run a link-check: search all `.md` files for `[[wikilinks]]` that reference old paths from this batch
- Report: N files moved, N broken links detected
- If broken links found: list them and ask whether to continue or pause for manual fix

Do NOT delete any old folders yet — leave them empty after moves so the user can verify in Obsidian before cleanup.

---

## Phase 5: Post-move verification

After all moves for the week are complete, run a full check:

1. **Broken wikilinks**: Search all `.md` files for `[[` references to old paths from this week's migration
2. **Broken Dataview queries**: Search for `FROM "notes/` lines that still reference old paths
3. **Missing files**: Confirm every file in the move plan landed at its destination

Output a verification report:
```
VERIFICATION REPORT — WEEK N
✅ N files confirmed at destination
⚠️ N broken wikilinks found: [list]
⚠️ N Dataview queries still reference old paths: [list]
```

---

## Phase 6: Mark week complete

If verification passes (or user confirms they're satisfied):

Update the migration status table in `notes/40 Areas/pkm/vault-architecture-v2.md`:
- Change the week row from `⏳ Pending` to `✅ Complete (YYYY-MM-DD)`

Show the exact diff before writing. Ask for confirmation before modifying the file.

Also output a reminder checklist of any manual actions that couldn't be automated (plugin config changes, frontmatter additions, folder deletions).
