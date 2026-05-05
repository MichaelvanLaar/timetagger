# TimeTagger

Open-source time-tracker web app. Python backend (uvicorn/asgineer/SQLite) + frontend in Python compiled to JavaScript via PScript.

## Key Config Files

| File | Purpose |
|------|---------|
| `CLAUDE.md` | Project instructions, loaded every message |
| `.claude/settings.json` | Permissions, hooks, environment variables |
| `.claude/skills/cc-init/SKILL.md` | Skill: bootstrap Claude Code config for new projects |
| `.claude/skills/cc-optimize/SKILL.md` | Skill: audit and optimize existing Claude Code config |
| `.claude/skills/cc-update/SKILL.md` | Skill: update cc-\* skills to latest versions |
| `.claude/skills/openspec-apply-change/SKILL.md` | Skill: implement tasks from an OpenSpec change |
| `.claude/skills/openspec-archive-change/SKILL.md` | Skill: archive completed OpenSpec changes |
| `.claude/skills/openspec-explore/SKILL.md` | Skill: explore ideas and investigate problems |
| `.claude/skills/openspec-propose/SKILL.md` | Skill: propose new OpenSpec changes with all artifacts |
| `.githooks/pre-commit` | Keeps Key Config Files table in sync |
| `.github/workflows/ci.yml` | CI: lint + multi-Python test matrix |
| `.github/workflows/dockerimage.yml` | Docker image build workflow |
| `.gitignore` | Git ignore patterns |
| `.readthedocs.yaml` | Read the Docs build configuration |
| `requirements.txt` | Runtime dependencies |
| `scripts/sync-config-table.sh` | Syncs Key Config Files table in CLAUDE.md |
| `setup.py` | Package metadata and install config |
| `tasks.py` | Invoke task runner (lint, format, test) |

## Commands

- `pytest tests/` — run test suite
- `invoke lint` — flake8 linting
- `invoke checkformat` — verify Black formatting (non-destructive)
- `invoke format` — auto-format with Black
- `python -m timetagger` — run local dev server

## Structure

- `timetagger/` — main package (server, app, common, pages)
- `timetagger/app/` — frontend Python compiled to JS via PScript
- `tests/` — pytest test suite
- `tasks.py` — invoke task definitions
- `openspec/` — OpenSpec change management workflow

## Conventions

- `timetagger/app/*.py` is frontend code — it gets compiled to JS by PScript; browser APIs are valid there
- Black enforces formatting; flake8 enforces style — don't add rules already covered by these tools

## Don't

- Don't commit secrets or credentials to git
- Don't use `--force` flags — fix the underlying issue instead

## Learnings

When the user corrects a mistake or points out a recurring issue, append a one-line summary to `.claude/learnings.md`. Don't modify CLAUDE.md directly.

## Compact Instructions

When compacting, preserve: list of modified files, current test status, open TODOs, and key decisions made.
