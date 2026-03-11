# Filing

Rules for filing and organizing information — notes, tasks, calendar events, and reminders.

## Inbox

**Inbox directory:** `user/Inbox/`

Incoming items to be processed. Use the `/process-inbox` skill to work through it. Progress is tracked in `docs/inbox-progress.md` — update it after each session.

## Notes

**Notes directory:** `user/Notes/`

- **Create notes freely** when directed to, or when it clearly makes sense to (e.g., capturing research, a decision, or something worth filing). Don't ask for permission if the intent is obvious.
- **Always open notes after creating them** so the user can review and edit.
- **Only write facts, not interpretations.** Don't add "why this matters" or your own analysis. Stick to what the source says or what the user tells you.

### Wikilinks

Use just the note title: `[[File Title]]`. Only include the directory path if needed for disambiguation.

### Tags

Use existing tags only. Tags are always `#hashtags` inline in the note body (directly under the `#` heading), not YAML frontmatter arrays. If none of the existing tags fit and a new one seems warranted, don't just create it — say why a new tag is needed and suggest a few name options for the user to pick from.

**Be thorough with tags.** When creating or editing a note, review the full list of existing tags and apply every relevant one — not just the most obvious. A hardware product about audio privacy should get `#products #privacy #security #ai` etc., not just `#privacy`. Think about: what is it (product, article, person), what domains it touches (ai, design, web), and what topics it relates to (privacy, agents, computing).

### Clippings

Clippings use **no frontmatter**. Structure: `# Title`, then `#tags` on the next line, then the source URL, then content.

**Naming:** Formal/literature sources use `{Title} ({Author}, {Year}).md`. Everything else (blog posts, news, tweets, etc.) uses a prose-like descriptive title — e.g., `Nabeel Hyatt's CoworkPowers for Claude.md`, `AI agent publishes hit piece on open-source maintainer.md`. Keep it casual and readable.

Before adding tags to a note, discover existing tags in the vault:

```bash
grep -roh '#[a-zA-Z][a-zA-Z0-9_/-]*' ~/Workspace/user/Notes/ | sort -u
```

### Assets

Images and videos go in `Assets/`. Reference with wikilinks: `![[filename.png]]` (no folder prefix unless needed for disambiguation).

**Naming:** Use lowercase, hyphenated, simple descriptive names — e.g., `nova-lightmode.png`, `arc-browser.png`. No spaces, no dates, no uppercase.

Convert videos to GIF before adding:

```bash
ffmpeg -i video.mp4 -vf "fps=10,scale=480:-1:flags=lanczos" -loop 0 Assets/name.gif
```

## Shared links (videos & articles)

When the user shares a link they want to watch or read:

1. **Save a `.webloc` file** to `~/Dropbox/Read Later/` (or `Videos/` subfolder for videos) — this is the default action
2. **If urgent (this week):** add a link to To-Do.md instead of (or in addition to) saving a webloc
3. **If project-related but not urgent:** add to the relevant `Planning/` file
4. **Don't download videos** unless explicitly asked to download

`.webloc` format (XML plist):
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>URL</key>
	<string>https://example.com</string>
</dict>
</plist>
```

## Tasks & GTD

Loose GTD-style system managed via the `/review` skill. Items go to different places depending on timing and type:

| What | Where |
|------|-------|
| Undated tasks (next actions) | `To-Do.md` |
| Dated tasks (do on/at a specific day/time) | Apple Reminders (`remindctl`) — all-day unless time specified |
| Meetings & events | Google Calendar → **primary** calendar |
| Push notifications ("remind me to...") | Apple Reminders (`remindctl`) |
| Area planning (focus/later/someday) | `Planning/{Area}.md` |
| Coming up / on the radar | `Planning/On my radar.md` (dated by month + "Up next" for undated) |
| People to reach out to | `Planning/Networking.md` |
| Project status | `Planning/{Name}.md` or `To-Do.md # Projects` for minor ones |

### To-Do.md

The weekly working list — only items explicitly promoted during review. Not a dump for all to-dos; everything else lives in Planning/. Sections: **# Today**, **# Priorities**, **# Actions**, **# Waiting**, **# Projects**.

- Add concrete, one-step next actions under **# Actions**
- `(flg.)` after an item means it's flagged in email — look there for the thread
- Use `With Person:` and `At Location:` subheadings to batch by GTD context. `With Person/Team:` sections are **discussion agendas** (things to raise with someone). `At Location:` sections are context-dependent solo work items (things to do when you're there).
- In To-Do.md, colons are for context headings only — don't use `Person: thing` format in task text.
- Move completed items out (don't leave them checked off)
- Items with a specific date → add as an Apple Reminder instead

#### Today section

Lives at the top of To-Do.md. Constructed during daily review, replaced each day.

- **One paragraph** at the top: calendar shape, what to focus on and why. Opinionated, short. No date needed.
- **`<u>underline</u>`** for parent items that have subtasks — it's a hierarchy marker, not emphasis. This applies across all of To-Do.md, not just Today.
- **Subtasks** (indented `- [ ]`) only when a parent breaks into distinct steps. Use tabs for indentation.
- **Sections** (`**Core work:**`, `**Home:**`, etc.) only when the list is long enough to need grouping or there are distinct contexts to separate. Not always needed.
- **Items in Today are moved out of Actions** — no duplication. Uncompleted items move back at end of day.
- Calendar events stay on the calendar — don't list them as tasks.

### Adding items

When the user adds an item and hasn't specified timing or type, ask succinctly:

1. **When?** — ASAP (→ To-Do.md), specific date/time (→ Tasks calendar), or later (→ Planning/)
2. **Project or next action?** — If unclear, ask whether this is a single action or part of a larger effort

### Planning/

All plans, projects, and area files live flat in `Planning/`. No separate Projects/ folder — everything in one place. Planning/ is the centralized planning layer — substantive notes (research, specs, decisions) live in the vault by topic (e.g. `Telepath/Television/`, `Personal/Finances/`). Plans don't need to link to associated notes unless there's actionable information there.

Files are freeform — high-level planning up top, items roughly prioritized. No required sections. Weekly: sweep Planning/, promote due items to To-Do.md.

Next actions (checkboxes, `- [ ]`) belong on To-Do.md, not in Planning/ files. Those files can have **next steps** as plain dot points to indicate direction, but the actual actionable items live on To-Do.md.

Use `==highlights==` to flag priority items in Planning/ files — things that are committed and important but not actionable this week.

Minor projects (single outcome, no complex planning) just go in the **# Projects** section of `To-Do.md` — don't create a standalone file.

**Every project must have a next action** on the Actions list — but not inline in the project entry.

**Project entry format:** Project name with brief status where helpful — enough to know where things stand at a glance. No next actions inline. Link to the plan with wikilinks when one exists. Examples:
- `Redirect mail from our old house`
- `Get achy fingers checked out`
- `[[Television]]: refining styling`
- `[[Telepath branding]]: waiting on quote`
- `Arrange walk with Pam: waiting for her response`

### Technical projects

For code projects (repos), tracking works as follows:

- **Planning/{Name}.md** is the source of truth — status, direction, ideas. Links out to everything else.
- **GitHub Issues** are for concrete bugs and dev tasks that can be picked up.
- **Team coordination** stays in Company Priorities docs.
- **Next actions** live on To-Do.md as always.

Don't use repo `TODO.md` files — they're a third place to lose things. Migrate anything useful into Planning/ (ideas/direction) or GitHub Issues (concrete/actionable), then delete the file.

Each plan file should note where else tasks are tracked (e.g. GitHub Issues URL) so everything is findable from one place.

**Project vs. action:** A project is anything that requires more than one physical next action. If it can't be done in one step, it's a project — add it to `To-Do.md # Projects`. Only create a standalone plan file in `Planning/` when there's enough detail to warrant it, and always check with the user before creating one.

**Proactively identify projects.** When processing inbox items or adding tasks, think about whether the item implies multiple steps (e.g. "doctor situation" = book appointment → get diagnosed → follow up). If so, treat it as a project from the start rather than filing it as a single action.

## Calendars

### Tasks calendar (deprecated)

No longer used for dated tasks. Use Apple Reminders (`remindctl`) instead — all-day by default.

### Important calendar

Use the **Important** calendar for deadlines and key dates:

- **Calendar ID:** `951ef6330f1f380153dc114f3193ca1ce79093f3afdfc47e73f55e12f35b249d@group.calendar.google.com`
- All-day events marking deadlines (e.g. "Article due", "Demo must be posted")

### Day focus

- **Work focus** → all-day event on the **Telepath** calendar (`rupert@telepath.computer`)
- **Personal focus** → all-day event on **primary** calendar

### Calendars to check

When reviewing or checking schedule, check all calendars: primary, Family, Tasks, Important, Telepath, Mina, Community, Izzi.

## Reminders

Apple Reminders via `remindctl` — used for dated tasks and push notifications:

```bash
remindctl add --title "X" --due "2026-02-24 15:00"
```
