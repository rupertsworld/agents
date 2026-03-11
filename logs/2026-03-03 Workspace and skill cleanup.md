# Workspace and skill cleanup

Major restructuring of the agents repo to separate generic, shareable skills from personal configuration and documentation. The repo is now positioned as the canonical workspace, with personal details extracted to `docs/` and skills made portable.

## Goal

Separate implementation-specific details (calendar IDs, filing rules, personal config) from the skills themselves, so skills are generic and shareable while docs hold the personal configuration. Eventually, `skills/` could be published as a public repo.

## Key decisions

### The repo *is* the workspace
Rather than having a separate workspace that symlinks into the repo, the repo itself is the workspace. Agents add local/ephemeral content (like `user/`) on top. The workspace at `~/Workspace` symlinks into the repo for `AGENTS.md`, `docs/`, `logs/`, and `skills/`.

### Skills reference docs loosely
Skills say "refer to any provided documentation" rather than naming specific doc files. `AGENTS.md` is the routing layer — it has a "Skills" section that maps each skill to its relevant docs (e.g. `/review`: see `docs/filing.md` for calendar IDs). This keeps skills portable.

### `user/` as the mount point name
Discussed alternatives (`mount/`, `local/`, `files/`) — settled on `user/` because it clearly signals "this is the user's space, not the agent's" which is the meaningful distinction for the agent.

### Code workflow redesigned
Previously: one `/code` parent skill with 4 sub-phases as one-liner redirects. Now: 3 standalone skills reflecting the actual workflow:
- `/code-spec` — structured Q&A in 3 stages (behavior → implementation approach → write spec), each requiring explicit approval before proceeding. Supports changesets for incremental spec changes.
- `/code-implement` — review spec → write ALL tests first → implement until passing → comprehensive spec adherence review. Stop and flag if spec is wrong.
- `/code-review` — review received code for spec adherence, design quality, clean code. Issues flagged as blocker/suggestion/nit.

Removed `/code-research` (folded into spec phase) and `/code-validate` (replaced by the review step in implement + the new code-review skill).

### Memory skills consolidated
`remember` (write persistent context) + `history` (search logs) merged into `/memory` — one skill for both reading and writing persistent context. `/save` renamed to `/log-session` for clarity.

## What was killed

| Skill | Reason |
|-------|--------|
| `open` | One line of bash + Obsidian URI. Not a skill. |
| `notetaking` | Stale, superseded by `notes` (which itself became `docs/filing.md`). |
| `health-check` | Entirely local setup checks (`~/Repos/system`, `launchctl`). Not shareable. |
| `scratchpad` | `docs/` serves this purpose. Noted in `~/Desktop/notes.md`. |
| `code` (parent) | Sub-skills are standalone now. |
| `code-research` | Folded into spec phase. |
| `code-validate` | Replaced by review step in implement + code-review skill. |

## What moved to docs

| Content | From | To |
|---------|------|----|
| Remote server details | `skills/remote/` | `docs/remote.md` |
| Filing rules, GTD, calendars, tasks, reminders | `skills/notes/` + `skills/agenda/` | `docs/filing.md` |
| Code style preferences | `skills/code/references/` | `docs/codegen/` |

`docs/filing.md` is the biggest doc — it absorbed content from both `notes` and `agenda` skills, including the Tasks calendar ID, calendar names to check, To-Do.md structure, Apple Reminders usage, and day focus conventions.

## What was renamed

| Old | New |
|-----|-----|
| `save` | `log-session` |
| `history` + `remember` | `memory` |
| `code-validate` | `code-review` (rewritten) |

## Structural changes

- Created `docs/` directory in repo, symlinked to `~/Workspace/docs`
- Created `logs/` directory in repo, symlinked to `~/Workspace/logs`
- Removed `~/Workspace/inbox` (not ready to deal with yet)
- Fixed broken symlink: `~/.claude/CLAUDE.md` was pointing to non-existent `/Users/rupert/Repos/system/agents/AGENTS.md`, now points to `/Users/rupert/Repos/agents/AGENTS.md`
- Simplified `~/.claude/skills` symlink (was going through `~/.agents/skills` intermediary)
- Removed recursive symlink `skills/skills → skills`
- Stripped `user-invocable` and `allowed-tools` from all skill frontmatter (framework-specific, not generic)

## Symlink state

```
~/.claude/CLAUDE.md    → /Users/rupert/Repos/agents/AGENTS.md
~/.claude/skills       → /Users/rupert/Repos/agents/skills
~/Workspace/AGENTS.md  → /Users/rupert/Repos/agents/AGENTS.md
~/Workspace/docs       → /Users/rupert/Repos/agents/docs
~/Workspace/logs       → /Users/rupert/Repos/agents/logs
~/Workspace/skills     → /Users/rupert/Repos/agents/skills
```

## AGENTS.md changes

- Removed detailed workspace subdirectory descriptions (docs/, logs/, inbox/, skills/ sections)
- Removed inbox reference
- Added "Important references" section linking to `docs/filing.md`, `docs/codegen/`, `docs/remote.md`
- Added "Skills" section with per-skill config (e.g. `/read-later`: save to `~/Dropbox/Read Later`)
- Simplified Remote section to just point to `docs/remote.md`

## External actions

- Created GitHub issue [telepath-computer/stash#1](https://github.com/telepath-computer/stash/issues/1) for `.stashignore` and `.gitignore` support — needed for the repo-as-workspace model where ephemeral dirs (`logs/`, `user/`) should be ignorable.

## Parked in tmp/

- `agentmail` — third-party email platform skill. Undecided.
- `calendar` — Fastmail CalDAV via vdirsyncer + khal. Remote-only, very personal. May be removed.

## Open items

- `~/Desktop/notes.md` has notes on:
  - Skill directory reconciliation (merging skills from multiple sources)
  - `docs/` as scratchpad replacement
- `TODO.md` has:
  - Build/install step to compile workspace per environment (resolve paths, set up symlinks)
- Stash needs `.stashignore` support before this repo can cleanly sync with ephemeral dirs excluded
- `jobs/inbox-filer.md` still references `~/Workspace/inbox` — inbox feature is on hold
