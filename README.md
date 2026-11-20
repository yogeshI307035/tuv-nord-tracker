# TÜV NORD · Topic Tracker

Kanban view of SAP Sales Cloud V2 topics for TÜV NORD, auto-refreshed from SharePoint daily.

🔗 **Live:** https://yogeshi307035.github.io/tuv-nord-tracker/
🔙 **Back to PM Dashboard:** https://yogeshi307035.github.io/pm-dashboard-v2/

## Source
`TÜV NORD Topic Tracker v2.xlsx` on SharePoint site 211047. Share link cached in `~/PM-Dashboard/tuv-nord-tracker/refresh.sh`.

## Pipeline
Same model as the Bosch tracker:
1. Chrome CDP on :9222, signed in to sap.sharepoint.com (automation profile)
2. `refresh.sh` resolves the share link via `/_api/v2.0/shares/{share_id}/driveItem`, downloads bytes
3. `parse.py` → `data/data.json`
4. Script copies `index.html` + `data.json` into this repo, commits + pushes
5. GitHub Pages redeploys in ~30-60s

## Notes
Per-row notes live in browser `localStorage['tuv-nord-tracker-notes-v1']`, keyed by `sha1(topic+criticality)[:12]` so refreshes preserve them.
