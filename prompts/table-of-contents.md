# Cheatham County Project — Table of Contents

Compiled 2026-09-11. Index of what exists in this project and where to find it.

## Core files
- [Context.md](../Context.md) — project goal, what "good" looks like, rules
- [references.md](../references.md) — inventory of every board/commission per jurisdiction, with website links
- [Tracking.md](../Tracking.md) — grid of what minutes are on file per board per month

## Minutes (source docs + summaries)
Organized by month under `Minutes/YYYY-MM/`. Each month has a `_Summary` file plus raw PDFs/HTML minutes. As of 2026-09-11, this project only pulls approved minutes going forward — agendas are no longer collected or tracked (see `Prompts/Monthly Minutes Pull.md`). Agenda files from before that policy change remain in the Jun-Sep 2026 folders.

| Month | Summary | Status |
|---|---|---|
| June 2026 | [Minutes/2026-06/_Summary - June 2026.md](../Minutes/2026-06/_Summary%20-%20June%202026.md) | Complete pull |
| July 2026 | [Minutes/2026-07/_Summary - July 2026.md](../Minutes/2026-07/_Summary%20-%20July%202026.md) | Complete pull |
| August 2026 | [Minutes/2026-08/_Summary - August 2026.md](../Minutes/2026-08/_Summary%20-%20August%202026.md) | Some minutes still pending |
| September 2026 | [Minutes/2026-09/_Summary - September 2026.md](../Minutes/2026-09/_Summary%20-%20September%202026.md) | Partial — month in progress at pull time |

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
- Data centers are a recurring cross-board topic (Planning Commission, Kingston Springs, County budget hearing) worth continued tracking.

## Prompts
This folder (`Prompts/`) holds reusable prompt files for recurring tasks.
- [Monthly Minutes Pull.md](Monthly%20Minutes%20Pull.md) — full process for pulling a new month's minutes across every board, including the manual Board of Education download step.

Related skill: `/pull-boe-minutes` (`.claude/skills/pull-boe-minutes/`) — checks BOEconnect for new BOE meetings and returns a checklist, since that site blocks scripted downloads.
