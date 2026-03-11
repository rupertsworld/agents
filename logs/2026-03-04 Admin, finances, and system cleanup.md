# 2026-03-04 Admin, finances, and system cleanup

## What happened

A wide-ranging admin session that started with MozAlums comms and snowballed into a deep financial review, notes reorganization, and several system improvements.

## MozAlums & Dees

- Dees sent a message about a MozAlums meetup at Kathy's place near Stanford Dish, **Saturday March 7 at 3pm**. Added to calendar.
- Responded to Dees about meeting up — now waiting on him for breakfast timing so we can connect after.
- Added "Respond to MozAlums intro thread (flg.)" to Actions.
- Learned and persisted: MozAlums is the ex-Mozillian alumni community headed by Dees. Dees visits the Bay Area periodically. `(flg.)` convention means the item is flagged in email.

## Financial review

Major session working through the financial picture. Key findings:

- **Amex Gold ~$15k** — revolving monthly spend, not real debt. Paid each cycle to get back down to ~$7k. The stress point is the Mar 18 payment ($7,336) vs paycheck timing (Mar 6 & Mar 20 — 2 days late).
- **Freedom Unlimited ~$7,100** — real debt from rent & school fees catch-up. Minimums are only ~$200/month, first due Apr 16. Not urgent.
- **Wells Fargo $7k** — needs zeroing out long-term.
- **Monthly income:** ~$13,500. **Burn:** ~$12,000 (after school fees stopped). **Surplus:** ~$1,500.
- School fees have just stopped, which is what brought burn from ~$13.5–14k down to $12k.
- Considering moving to Australia mid-year, which would reduce expenses significantly.
- **IRS refund (~$10k+)** is the main lever — call IRS at 1-800-830-5084 to get it moving.
- Created detailed Finances.md with summary, what's owed, key dates, plan by scenario, outstanding payments (Google Fi, Digital Ocean, Delaware/Desktop Metaphors, CommBank loan), and card strategy (consolidate to Amex Gold & Wells Fargo only, pay off Izzi's cards).

### New financial projects added to To-Do
- CommBank loan payment — overdue from end of Feb, multi-step (wait for Amex to clear Chase or Friday paycheck → determine amount → transfer to AU → pay)
- ATO payment — 2FA not working, need to call (+61 1300 306 105)

## Notes reorganization

Unified `Projects/` into `Planning/` (now renamed `Plans/`). Everything flat in one folder.

- Merged Projects/Stash.md into Planning/Stash.md (combined bugs, next steps, and future ideas)
- Merged Projects/Cashflow.md into Finances.md (income details, IRS phone number, outstanding payments)
- Moved Agent setup, Agent UI, Standards participation, Telepath branding, Telepath user testing, Website into Planning/
- Trashed empty Projects/ folder and duplicate files
- Updated AGENTS.md, filing.md, go.md references from Planning/ → Plans/

### Filing rule added
**Project vs. action:** Multiple dependent steps = project in To-Do.md # Projects (not necessarily a Planning/ file). Only create a standalone file in Plans/ when there's enough external reference detail, and always check with the user first.

## New skill: `/go`

Created a quick-launcher skill for bookmarks and frequent files.

- `skills/go/SKILL.md` — parses shortcut names, opens files or URLs, proactively persists new shortcuts
- `docs/go.md` — saved shortcuts with name, description, and target
- Symlinked `~/Dropbox/Shortcuts` → `user/Shortcuts`
- Indexed .webloc files: github, notion, tldraw, ynab, claude-code, progressive
- Added manual entry: clarity (La Scuola parent portal)
- Key design decisions: opens URLs directly (`open` on macOS), extracts from .webloc via `plutil`, saves shortcuts proactively (don't wait to be asked), stores path if known or description if not

## Other items

- Saved Harper's article "Child's Play" by Sam Kriss to Read Later
- Set up Friday reminder for Priyanka cash transfer (remindctl)
- Discovered remindctl doesn't support all-day reminders — it's a compiled Swift binary from steipete/remindctl. Added a project to clone and add --all-day support. Wrote a prompt for another agent to do the work.
- Added two 1-hour writing blocks to tomorrow's calendar (9:30–10:30am and 2–3pm)
- Today's progress at 3pm: lots of admin done, but Television UI and IRS call (the two core items) still need to happen

## Files changed

- `docs/filing.md` — added `(flg.)` convention, project vs action rule, Planning/ → Plans/
- `docs/go.md` — created, shortcuts registry
- `skills/go/SKILL.md` — created
- `AGENTS.md` — added /go skill, Planning/ → Plans/
- `user/Notes/Plans/Finances.md` — major rewrite with summary, scenarios, card strategy
- `user/Notes/Network/Dees.md` — updated with meetup details
- `user/Notes/Network/MozAlums.md` — updated description, linked to Dees
- `user/Notes/To-Do.md` — multiple updates throughout session
- `user/Shortcuts` — symlinked to ~/Dropbox/Shortcuts

## Open / next

- IRS call today (1-800-830-5084)
- Television UI coding today
- Pick article topic tonight
- Writing blocks tomorrow (9:30am & 2pm)
- Asena follow-up summary in next day or two
- remindctl all-day support (project)
- CommBank & ATO payments to action
- Discuss finances with Izzi / set aside time
