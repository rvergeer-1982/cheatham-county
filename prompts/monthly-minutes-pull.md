# Monthly Minutes Pull — Process

The full process for pulling a new month's board/commission minutes into `Minutes/YYYY-MM/`. Most boards can be pulled directly; the Board of Education cannot (see Step 5).

**Do not pull agendas.** As of 2026-09-11, this project only collects approved minutes. If a board's meeting has no approved minutes posted yet, leave it out entirely — do not download the agenda as a placeholder, and do not note it in `Tracking.md` as pending. Just skip it; it'll show up as a gap to check on the next pull.

## 1. Check what's already on file

Read `Tracking.md` to see the latest meeting date pulled per board. Any `—` cell is a candidate to check.

**Look back up to 3 months, no further.** Boards sometimes post minutes late, so a `—` cell from a prior month may have since been filled in. When doing a given month's pull, also re-check `—` cells for the **three months immediately prior** (e.g., pulling October also re-checks July, August, September). Do not look back further than that — a `—` cell older than 3 months stays as-is and isn't re-checked as part of the routine monthly pull. This doesn't apply to Nashville Electric Service, which has its own "not backfilled before 2026-09-11" rule (see Step 4).

## 2. Check `references.md` for the board list and source links

`references.md` has the official website/minutes-page link for every board in each jurisdiction:
- Cheatham County (government)
- Ashland City
- Kingston Springs
- Pleasant View
- Pegram
- Nashville Electric Service (NES) — the power utility, not a county/municipal body, but tracked the same way (see Step 4)

## 3. Pull new minutes for every board except Board of Education

For each board, open its Agendas & Minutes page (or general boards-and-commissions index if no dedicated page exists) and check for **approved minutes** for meeting dates not yet in `Minutes/YYYY-MM/`. These sites generally serve direct PDF/HTML links, so:

1. Identify the direct document URL for the minutes (not the agenda) of any new meeting.
2. Download directly (`Invoke-WebRequest` or WebFetch, whichever renders the real content — check the saved file isn't just a page shell before trusting it).
3. Save into `Minutes/YYYY-MM/` using the existing naming convention: `<Jurisdiction> - <Board> - YYYY-MM-DD.pdf`.
4. **If only an agenda exists and minutes haven't been posted yet, skip that meeting entirely.** Don't download the agenda, don't create a placeholder file, and don't add a note about it — it'll simply show as a gap in `Tracking.md` until minutes exist.

## 4. Pull new Nashville Electric Service (NES) minutes

NES's Electric Power Board and Audit & Ethics Committee minutes are posted as direct PDF links on [Our Board](https://www.nespower.com/our-board/#be992d8d-1f69-4847-92ef-18c880180896) — confirmed 2026-09-11 to be directly downloadable (no JS-viewer gating like BOEconnect), so this one can be scripted like the county/city boards in Step 3. One difference: filenames are inconsistent month to month (e.g. "power-board-minutes---july-2026.pdf" vs. "signed-legal-minutes-with-appendix-a--june-24-2026.pdf"), so locate each month's exact link on the page rather than guessing a URL pattern. Save using the same naming convention: `Nashville Electric Service - Electric Power Board - YYYY-MM-DD.pdf`.

**Added 2026-09-11 — not backfilled.** Per instruction, only pull NES minutes for meetings from this point forward; do not go back and pull its Jun–Sep 2026 minutes.

## 5. Pull new Board of Education minutes (manual step required)

BOEconnect (meeting.boeconnect.net) blocks scripted downloads — its server returns `canDownload: false` to anything that isn't a real browser session, confirmed by testing 2026-09-11. **Do not attempt to script this.** Use the `/pull-boe-minutes` skill instead:

1. It fetches the current BOEconnect meeting list and diffs it against what's already saved, looking only at **Minutes** links (not Agenda links).
2. It also flags any existing local `.html` BOE minutes files as likely broken (the JS viewer problem) even if they were never flagged before.
3. It returns a checklist: date, direct minutes link, and the exact filename/folder to save into. Meetings with no minutes link yet are left off the checklist entirely.
4. **You open each link in a real browser** and use the PDF viewer's own Download button (not "Save Page As") — save as `.pdf` using the given filename, into the given month folder.
5. Tell Claude when the files are saved. Claude will then:
   - Move/rename them if needed and delete any broken `.html` version they replace.
   - Read the real PDF content and update the relevant monthly `_Summary - <Month> <Year>.md` and `Tracking.md`.

## 6. After all boards are pulled

1. Update `Tracking.md` — mark ✅/— for each board/month cell. No agenda-only status.

**Note on past months (Jun–Sep 2026):** These were pulled under the old process and still include agenda files and agenda-based narrative in their summaries. That existing content was left as-is when this policy changed — the no-agenda rule applies going forward only.
