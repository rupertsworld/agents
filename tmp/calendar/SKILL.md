---
name: calendar
description: "Read, create, edit, and delete calendar events via Fastmail CalDAV (vdirsyncer + khal). Sync before reading and after writing."
metadata: { "openclaw": { "requires": { "bins": ["vdirsyncer", "khal"] } } }
---

# Calendar Skill

Fastmail CalDAV calendar via vdirsyncer + khal.

## Setup

- **vdirsyncer config:** `opt/config/vdirsyncer/config`
- **khal config:** `opt/config/khal/config`
- **Calendar data:** `opt/data/calendar/`
- **Env for vdirsyncer:** `VDIRSYNCER_CONFIG=/root/.openclaw/workspace/opt/config/vdirsyncer/config`
- **Env for khal:** `XDG_CONFIG_HOME=/root/.openclaw/workspace/opt/config`

## Always Sync Before and After

Before reading or writing calendar data, sync first. After any writes, sync again to push changes.

```bash
VDIRSYNCER_CONFIG=/root/.openclaw/workspace/opt/config/vdirsyncer/config vdirsyncer sync fastmail
```

## Reading Events

List events for a date range:

```bash
XDG_CONFIG_HOME=/root/.openclaw/workspace/opt/config khal list today 7d
```

Other useful variants:
- `khal list today` — just today
- `khal list tomorrow 1d` — tomorrow
- `khal list 2026-03-01 3d` — specific date range

## Creating Events

```bash
XDG_CONFIG_HOME=/root/.openclaw/workspace/opt/config khal new [-a CALENDAR] "YYYY-MM-DD HH:MM" "YYYY-MM-DD HH:MM" "Event title"
```

- `-a CALENDAR` selects which calendar (Personal, Family, Important, etc.)
- Default calendar is Personal
- All-day: `khal new -a Personal 2026-03-01 "Day off"`

## Editing Events

Use `khal edit` for interactive editing, or `khal list -f "{uid}"` to get UIDs and edit the .ics files directly in `opt/data/calendar/`.

## Deleting Events

Find the .ics file in `opt/data/calendar/` and delete it, then sync.

## Calendars

Mina, MLB, Izzi, Tasks, Notes, Invitations, Family, Important, La Scuola, Personal

## After Any Changes

Always sync after creating, editing, or deleting events:

```bash
VDIRSYNCER_CONFIG=/root/.openclaw/workspace/opt/config/vdirsyncer/config vdirsyncer sync fastmail
```
