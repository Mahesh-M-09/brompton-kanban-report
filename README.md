# Brompton Kanban Report

A production-ready browser dashboard for daily stores performance, trends, item analysis, picker performance, pick/delivery cycles and handover review.

## Data privacy

This repository contains the dashboard code only. It does **not** contain Kanban exports or operational transaction data.

The published dashboard reads a CSV selected by the user in Chrome or Edge. The browser remembers the selected file handle locally. The file remains on the user's computer or in a locally synchronised SharePoint/Teams folder and is never uploaded to GitHub.

## Using the shared dashboard

1. Open the GitHub Pages link in Chrome or Edge.
2. Select **Connect shared CSV**.
3. Choose the IT-controlled Kanban CSV from the locally synchronised SharePoint/Teams folder.
4. When IT replaces the file using the same filename, select **Refresh latest data**.
5. Select **TV full screen** for the live stores display. It shows a clock, the last data refresh and silently checks the connected file every five minutes by default.

## Configuration files

The `templates` folder contains two safe-to-share configuration files and no transaction data:

- `AreaConfig.csv` defines the clickable hierarchy: line (area), station (sub-area), rack and column.
- `ProductionCalendar.csv` defines weekly working days, shift times, breaks and dated exceptions. Connect it from **Production calendar** in the dashboard. A locally synchronised SharePoint/Teams copy can remain under IT control while the dashboard itself stays on GitHub Pages.

The dashboard uses the connected calendar when calculating working age. If no calendar is connected, its fallback is Monday–Thursday, 07:00–16:30, excluding 09:55–10:15 and 12:55–13:30.

## Print output

Open-request barcode and QR pick sheets are formatted for A5 portrait. Each side contains 10 requests, so duplex printing places 20 requests on one physical sheet; additional requests continue on later sides.

The browser may ask the user to allow file access again after a restart. If the file is moved or renamed, reconnect it.

## Publishing with GitHub Pages

In the repository, open **Settings → Pages**, choose **Deploy from a branch**, then select the `main` branch and `/ (root)` folder.

## Supported browsers

Persistent file connections and silent refresh are designed for current Chromium browsers, particularly Microsoft Edge and Google Chrome. The normal CSV upload fallback remains available in other browsers.
