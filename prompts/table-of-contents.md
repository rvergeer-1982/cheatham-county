# Cheatham County Project — Table of Contents

Compiled 2026-09-11, updated 2026-10-07. Index of what exists in this project and where to find it.

## Core files
- [Context.md](../Context.md) — project goal, what "good" looks like, rules
- [references.md](../references.md) — inventory of every board/commission per jurisdiction, with website links
- [Tracking.md](../Tracking.md) — grid of what minutes are on file per board per month

## Minutes (source docs + summaries)
Source PDFs sit outside the repo in `cheatham-county/Minutes/YYYY-MM/`. Summaries sit in the repo under `summaries/`. Only approved minutes are pulled (no agendas since 2026-09-11). Agenda files from before that change remain in the Jun-Sep folders.

| Month | Summary | Status (as of 2026-10-07 pull) |
|---|---|---|
| June 2026 | [summaries/2026-06.md](../summaries/2026-06.md) | Complete pull |
| July 2026 | [summaries/2026-07.md](../summaries/2026-07.md) | Complete pull |
| August 2026 | [summaries/2026-08.md](../summaries/2026-08.md) | Updated 2026-10-07 with 7 newly posted minutes. Kingston Springs PC/DRC/Beer Board and BOE Aug 27 still pending |
| September 2026 | [summaries/2026-09.md](../summaries/2026-09.md) | 3 sets of minutes on file. Most boards have not posted yet |
| October 2026 | [summaries/2026-10.md](../summaries/2026-10.md) | Partial — month in progress |

## Jurisdictions covered
Cheatham County (government), Ashland City, Kingston Springs, Pleasant View, Pegram — full board list per jurisdiction is in `references.md`.

## What's been done so far
- Built a reference list of every known board/commission and its official web source.
- Pulled minutes/agendas for June–September 2026 into `Minutes/`.
- Wrote a monthly summary per pull: what happened, plus a "Flags/issues" section calling out inconsistencies, unresolved conflicts, or things needing corroboration.
- Started a tracker (`Tracking.md`) to show gaps — which boards have no minutes on file for a given month.
- Flagged open items: two boards found in files but missing from `references.md` (Kingston Springs Wastewater Board, Pleasant View Beer Board); several county standing committees with no dedicated web page.

## Known gaps / recurring issues to watch
- Board of Education minutes on BOEconnect load through a JS PDF viewer, so a plain fetch only saves an empty page shell — **resolved 2026-09-11** for Jun 4, Jun 29, Jul 9, and Aug 4 by downloading real PDFs by hand (see `Prompts/Monthly Minutes Pull.md` and the `/pull-boe-minutes` skill). Re-reading those files surfaced a real internal board/commission budget conflict (June) and two document errors in the BOE's own minutes (August) — see the June/August summaries.
- Several boards have never had minutes pulled at all (e.g., County BZA, Cheatham Development Association, JECD, Public Library Board).
- Data centers are a recurring cross-board topic. As of 2026-10-07: Kingston Springs has a 12-month moratorium in law (Aug 20), Ashland City Planning Commission recommended 18 months (Sept 21), the county has none.
- County 911 radio upgrade costs are landing on each town (Pleasant View $101,860.80, Pegram $98,851.20). Watch Kingston Springs and Ashland City for their figures.
- County library projects: $10.5 million estimate, about $500k in architect fees already approved, funding decision deferred to the September workshop. Watch September County Commission minutes.
- County finance turnover: Mayor, Director and Assistant Director of Accounts all left in August 2026.
- Open records worth requesting: Election Commission SB 232 policy text; Ashland City zoning ordinance changes approved Sept 21.
- Kingston Springs minutes post about a month late (attached to the next meeting's agenda). See note 5 in tracking.md for where each site keeps minutes.

## Prompts
This folder (`Prompts/`) holds reusable prompt files for recurring tasks.
- [Monthly Minutes Pull.md](Monthly%20Minutes%20Pull.md) — full process for pulling a new month's minutes across every board, including the manual Board of Education download step.

Related skill: `/pull-boe-minutes` (`.claude/skills/pull-boe-minutes/`) — checks BOEconnect for new BOE meetings and returns a checklist, since that site blocks scripted downloads.
