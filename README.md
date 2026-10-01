# BPA Job Board

A day-by-day reference board for upcoming Bonneville Power Administration (BPA) audiometric testing jobs. It shows every site's placeholder hold, flags days with more than one site, and links straight to each HubSpot deal and placeholder record.

Maintained by Joe Webb, Customer Success Specialist, MHD Health.

## What's on the board

- **Summary tiles:** upcoming site jobs, service days held, days with multiple sites, and days where a responder is double-booked.
- **Mini calendars:** one per month. Click a highlighted day to jump to it. Dots under each day show which Safety Responder is booked.
- **Day-by-day list:** each job shows site, city, hold time, deal close date, Safety Responder, and buttons to open the deal and the placeholder in HubSpot.
- **Filters:** search by site, city or responder, filter to one responder, or show flagged days only. Filters are not saved and reset when the page reloads.

## Color key

| Color | Meaning |
|---|---|
| Blue | One site that day |
| Amber | Multiple sites on the same day |
| Red | Multiple sites, and the same responder's hours overlap |
| Teal stripe / chip | Randy Harrison |
| Purple stripe / chip | Bradley Kearns |

Multi-day holds (for example HMEM and Ross Complex) appear on every day they cover and count toward that day's flag. They are treated as one continuous block from start to end, matching how the hold is stored in HubSpot.

## Times

All times match the HubSpot placeholders and are shown in **Mountain Time**, which is how MHD records holds. For Pacific Time sites (all Washington and Oregon locations), the local service time is one hour earlier. Kalispell (MT) and Burley (ID) are already in Mountain Time.

When a hold is confirmed, the deal's **WO Start Time - Local** and **WO End Time - Local** fields show the translated local time. Use those when communicating times to BPA.

## Data source

This page is a **snapshot**. It does not pull from HubSpot live.

- Placeholder holds: HubSpot Placeholder Jobs object
- Deals: A/M Pipeline - Renewal Business
- Snapshot date: see the "as of" date in the page header

Not shown on the board:

- Portland HQ (Environmental Group), Idaho Falls, Garrison and Construction Group B have no 2027 placeholder.
- The BPA 2027 umbrella deal has no placeholder. It is linked in the page footer.

## Updating the board

All job data lives in one list near the bottom of `index.html`, inside the `<script>` tag, named `JOBS`. Each line is one job:

```js
{site:"Chemawa",city:"Salem, OR",deal:286690971331,pj:336908049117,close:"2027-02-02",s:"2027-02-01T08:00",e:"2027-02-01T12:00",r:R},
```

| Field | What it is |
|---|---|
| `site` | Site name as it should appear |
| `city` | City and state |
| `deal` | HubSpot deal record ID |
| `pj` | HubSpot placeholder job record ID |
| `close` | Deal close date (YYYY-MM-DD) |
| `s` / `e` | Hold start and end, Mountain Time (YYYY-MM-DDTHH:MM, 24-hour clock) |
| `r` | Responder: `R` for Randy Harrison, `B` for Bradley Kearns |

To change a job, edit its line, then commit the change. To remove a job, delete its line. The summary tiles, calendars and flags recalculate automatically.

After you commit, GitHub Pages republishes in a minute or two. Refresh the page on any device to see the change.

## Known issues to resolve

- **Celilo:** the placeholder shows Tue 2/23/2027, but the renewal deal's Hold 1 is Wed 2/3/2027, 1pm-2pm. The placeholder is named after the 2026 Closed Won deal.
- **Service Time Zone blank** on 10 renewal deals: Big Eddy, Celilo, Chemawa, Keeler, North Bend, Alvey, Redmond, Malin, McNary and Burley. This may affect the local-time conversion when holds are confirmed.

## Privacy

This page contains customer site names, service dates, staff names and links into MHD's HubSpot. Keep the repository private and share access only with MHD staff who need it.
