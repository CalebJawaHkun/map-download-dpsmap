---
name: status-tracking
description: >-
  Use this skill whenever completing a task, feature, fix, or milestone in
  map-download-dpsmap to update STATUS.md with completed work, Added/Modified/Deleted
  file records, and git commit-cycle rollovers.
---

# Project Status Tracking (`STATUS.md`)

Record completed work in `STATUS.md` without checklists. Group entries by git commit cycle so contributors and agents can see everything added, modified, and deleted between commits.

## Workflow

1. **Inspect Git State:**
   Run:
   ```sh
   git rev-parse --short HEAD
   git log -1 --format="%h %s (%cs)"
   git status --short
   ```
2. **Roll Over Previous Uncommitted Cycle (if `HEAD` advanced):**
   Check `STATUS.md` under `## 3. Completed Work`.
   - If an `### Uncommitted (since <old-hash>)` heading exists and `<old-hash>` differs from current `HEAD`, run:
     ```sh
     git log <old-hash>..HEAD --format="%h %s (%cs)"
     ```
   - Rename that group heading to `### Commit <commit-hash> — <commit-subject> (<date>)` (or attribute across the listed commits if multiple commits landed in that cycle).
3. **Ensure Active Cycle Heading Exists:**
   - If no `### Uncommitted (since <current-HEAD>)` section exists at the top of `## 3. Completed Work`, create it directly above the latest committed group.
4. **Add Completion Entry:**
   Prepend a new entry directly under `### Uncommitted (since <current-HEAD>)` using this exact format:

   ```markdown
   #### YYYY-MM-DD HH:MM — <Short Completion Title> (`<Author / Agent>`)
   <1–2 sentence summary of what was completed and verified.>
   - **Added:**
     - `path/to/file` — <brief purpose>
   - **Modified:**
     - `path/to/file` — <what changed>
   - **Deleted:**
     - None
   ```

   - Record every file added, modified, or deleted **during that completion** (cross-checking `git status --short` / `git diff --name-status HEAD` so nothing is missed).
   - Explicitly write `- None` when a category (`Added`, `Modified`, or `Deleted`) has no changes.
5. **Sync Header & Decisions:**
   - Update `> Last updated: YYYY-MM-DD` and `## 1. Current Phase` if the project transitioned phases.
   - Append any newly locked architectural/UX decisions to `## 2. Locked Design Decisions`.
   - **Never** add markdown checklists (`- [ ]`, `- [x]`) or future `[TODO]` items to `STATUS.md`.
