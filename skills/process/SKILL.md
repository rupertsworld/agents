---
name: process
description: >
  GTD-style inbox processing. Pulls items from the user's inbox in batches of 5,
  then works through each one: what is it, is it actionable, where does it go.
  Use when the user says "process inbox", "process", "check inbox", "file inbox",
  or "what's in my inbox".
---

# Process Inbox

GTD inbox processing. Pull 5 items at a time from the user's inbox, then work through each one.

Refer to any provided documentation for filing rules, naming conventions, and tag usage.

## Setup

1. Read the filing documentation before processing anything.
2. List what's in the inbox. If empty, say so and stop.
3. Take the first 5 items (or fewer if less remain) as the current batch.

## For each item

Work through one item at a time. For each:

### 1. What is it?

Read, preview, or summarize the item. Present it to the user concisely — what it is, what it contains.

### 2. Is it actionable?

Ask the user. Two paths:

**Not actionable:**
- **Trash** — delete it (confirm first)
- **Reference** — file it as a note, clipping, or asset. Propose a destination, name, and tags per the filing rules.
- **Someday/maybe** — file to the appropriate planning area

**Actionable:**
- **Do it now** (< 2 min) — do it or let the user do it, then discard the item
- **Delegate** — add to waiting list, note who and when. Discard or file the item.
- **Defer** — what's the next action?
  - Has a specific date/time → schedule it on the calendar
  - No specific date → add to the task list
  - Is it a project (multi-step)? → create a project entry and define the first next action

### 3. File or act

Execute whatever was decided — move the file, create a note, add a task, schedule an event, or delete. Confirm before destructive actions.

## Between batches

After finishing 5 items, report progress (how many processed, how many remain) and ask if the user wants to continue with the next 5.

## Guidelines

- One item at a time — don't batch proposals.
- Keep it moving. Be concise in summaries, direct in proposals.
- Some items aren't notes — images, PDFs, downloads. Handle them appropriately.
- If an item should become a proper note (e.g., raw text, a URL), create the note and remove the original.
- If unsure where something goes, ask — don't guess.
