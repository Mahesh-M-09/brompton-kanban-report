# Brompton Kanban Report

A production-ready browser dashboard for daily stores performance, trends, item analysis, picker performance, pick/delivery cycles and handover review.

## Data privacy

This repository contains the dashboard code only. It does **not** contain Kanban exports or operational transaction data.

The published dashboard reads a CSV selected by the user in Chrome or Edge. The browser remembers the selected file handle locally. The file remains on the user's computer or in a locally synchronised SharePoint/Teams folder and is never uploaded to GitHub.

## Using the shared dashboard

1. Open the GitHub Pages link in Chrome or Edge.
2. Open **Admin** and enter the configuration password supplied to the Stores team.
3. Recommended: select **Connect data folder** and choose the locally synchronised SharePoint/Teams folder. The dashboard uses `KanbanExport.csv`; if that file is absent it uses the newest `ToExcel_ue_BBL_KanbanRpt*.csv`.
4. Alternatively, select **Connect one CSV** and choose a stable IT-controlled file. Drag-and-drop is session-only and cannot silently refresh after a restart.
5. Select **TV full screen** for the live stores display. It shows a clock, the last successful data refresh and checks the connected source every five minutes by default.

The browser stores only a file or directory permission handle. After a browser or computer restart, Chrome/Edge may require one click on **Refresh** to approve access again. Clearing site data, changing browser profile, moving the source, or renaming a directly connected file removes or breaks that remembered connection.

## Configuration files

The `templates` folder contains two safe-to-share configuration files and no transaction data:

- `AreaConfig.csv` defines the graphical hierarchy: line (area), station (sub-area), rack and column.
- `ProductionCalendar.csv` defines weekly working days, shift times, breaks and dated exceptions. Connect it from **Production calendar** in the dashboard. A locally synchronised SharePoint/Teams copy can remain under IT control while the dashboard itself stays on GitHub Pages.

The dashboard uses the connected calendar when calculating working age. If no calendar is connected, its fallback is Monday–Thursday, 07:00–16:30, excluding 09:55–10:15 and 12:55–13:30.

Calendar changes apply immediately in the open report but become permanent only after **Save Calendar**. With a writable file connection, Save replaces the connected CSV. With a session-only upload, the browser downloads `ProductionCalendar_updated.csv`; that downloaded file must replace the controlled `ProductionCalendar.csv`.

## Activity-window and transition logic

- Events are grouped by person and calendar date, then ordered strictly by timestamp.
- Changing from picking to delivery, or delivery to picking, always starts a new window.
- Consecutive activity of the same type starts a new window when working idle time exceeds the Admin threshold (10 minutes by default).
- Gap analysis measures each consecutive window transition once. It never matches by request or item.
- BS Pick scans (`ASL-STOCK` to `KAN-STAGING`) do not start a gap-analysis work window.
- Morning and lunch breaks are removed from transition time.
- Transition status is green at 5 minutes or less, amber above 5 through 15 minutes, and red above 15 minutes.
- Pick and delivery target counts and durations are configured in Admin and displayed beside actual window results.

## Print output

Open-request barcode and QR pick sheets are formatted for A5 portrait. Each side contains 10 requests, so duplex printing places 20 requests on one physical sheet; additional requests continue on later sides.

The browser may ask the user to allow file access again after a restart. If the file is moved or renamed, reconnect it.

## Publishing with GitHub Pages

In the repository, open **Settings → Pages**, choose **Deploy from a branch**, then select the `main` branch and `/ (root)` folder.

## Supported browsers

Persistent file connections and silent refresh are designed for current Chromium browsers, particularly Microsoft Edge and Google Chrome. The normal CSV upload fallback remains available in other browsers.
