# Cursor configuration
This repository syncs selected Cursor content (skills, rules, commands, and the **gh-skills** submodule) across machines.
## Clone with the submodule
This repo includes **`skills/gh-skills`** as a Git submodule. If you clone without initializing submodules, that folder stays empty until you update it.
**Recommended (one step):**
```bash
git clone --recurse-submodules https://github.com/fredericpoitevin/.cursor.git ~/.cursor
```
**If you already cloned without submodules:**
```bash
cd ~/.cursor
git submodule update --init --recursive
```
### SSH
```bash
git clone --recurse-submodules git@github.com:fredericpoitevin/.cursor.git ~/.cursor
```
## Submodule reference
| Path | Repository |
|------|------------|
| `skills/gh-skills` | [carbonscott/gh-skills](https://github.com/carbonscott/gh-skills) |
## After `git pull`
Fetch submodule commits that the parent repo points to:
```bash
cd ~/.cursor
git pull
git submodule update --init --recursive
```
