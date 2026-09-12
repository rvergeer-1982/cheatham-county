## Month End Summary and Distribution
1. Write or update `github-repo/summaries/YYYY-MM.md` — what happened, plus a Flags/issues section for inconsistencies, unresolved conflicts, or anything needing corroboration (per the project's skeptic rules in `context.md`).
   - **Policy changes:** for any board policy that was adopted, revised, or rescinded, give a brief description of what the policy actually does — not just its title/number.
   - **New changes:** for any new policy, program, fee, or rule change (not just a routine renewal or reaffirmation), note who is affected by it (e.g., students, a specific grade band, employees, a specific board/committee, the public).
2. Check for cross-board connections worth noting (same topic/person/dollar figure appearing in more than one board's minutes).
3. Update `prompts/table-of-contents.md` if new gaps or resolved gaps are worth flagging there.
4. Commit and push `github-repo/summaries/YYYY-MM.md` to GitHub once finished — the automated email (step 5) reads from the pushed repo, not the local file.
5. **Automated:** a cloud-scheduled agent emails the finished `summaries/YYYY-MM.md` to rob@vergeer.ca on the last day of the month, reading it from the `cheatham-county` GitHub repo. Set up 2026-09-11 — see the repo's GitHub Actions / scheduled agent config for the exact trigger.
   - If the summary for the current month hasn't been finished and pushed by month-end, the automation will email whatever is on GitHub at that point (or skip/flag if the file doesn't exist yet) — finish and push step 4 before the last day.