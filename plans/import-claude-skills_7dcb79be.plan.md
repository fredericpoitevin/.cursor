---
name: import-claude-skills
overview: Clone `carbonscott/.claude.git` via SSH, import its `skills/*/SKILL.md` into Cursor user-scope `~/.cursor/skills/*/SKILL.md`, and normalize frontmatter by adding missing `name:` fields so Cursor can discover the skills.
todos: []
isProject: false
---

## Steps
1. Clone the upstream repo via SSH
   - Run `git clone --depth 1 git@github.com:carbonscott/.claude.git <tempDir>` (use a temp directory, e.g. under `/tmp`).
   - Confirm `<tempDir>/skills/` exists.
2. Prepare Cursor destination
   - Ensure the destination root exists: `~/.cursor/skills/`.
3. Import skills
   - For each directory under `<tempDir>/skills/*`:
     - Read `<tempDir>/skills/<skillName>/SKILL.md`.
     - Create `~/.cursor/skills/<skillName>/`.
     - Copy `SKILL.md` to `~/.cursor/skills/<skillName>/SKILL.md`.
     - Frontmatter normalization:
       - If the YAML frontmatter is present but missing `name:`, insert `name: <skillName>` into the frontmatter (keep `description:` and any other existing frontmatter keys unchanged).
       - If `description:` is missing, log it for follow-up (do not guess).
4. Basic verification (post-import)
   - Verify each imported skill file contains frontmatter with both `name:` and `description:`.
   - Print a summary: imported skill count + which files had `name:` added.
5. Usage sanity check
   - In Cursor, trigger/try applying a couple imported skills by name (e.g., `clarify`, `approval`) and confirm they show up as available skills.

## Notes / Risks
- The upstream skills appear to use Claude-specific constructs (for example `$ARGUMENTS` and `AskUserQuestion`-style tool names). Importing them as-is should still work for Cursor’s markdown parsing, but tool/function names may not map perfectly; if you see failures during testing, we can do a targeted compatibility pass afterward.