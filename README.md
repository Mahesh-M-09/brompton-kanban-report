# Brompton Kanban Report

A browser-based Kanban operations dashboard for daily stores performance, trends, item analysis, picker performance, pick/delivery cycles and lost-time review.

## Data privacy

This repository contains the dashboard code only. It does **not** contain Kanban exports or operational transaction data.

The published dashboard reads a CSV selected by the user in Chrome or Edge. The browser remembers the selected file handle locally. The file remains on the user's computer or in a locally synchronised SharePoint/Teams folder and is never uploaded to GitHub.

## Using the shared dashboard

1. Open the GitHub Pages link in Chrome or Edge.
2. Select **Connect shared CSV**.
3. Choose the IT-controlled Kanban CSV from the locally synchronised SharePoint/Teams folder.
4. When IT replaces the file using the same filename, select **Refresh latest data**.
5. For a stores TV, choose an optional 2, 5 or 10 minute refresh interval.

The browser may ask the user to allow file access again after a restart. If the file is moved or renamed, reconnect it.

## Publishing with GitHub Pages

In the repository, open **Settings → Pages**, choose **Deploy from a branch**, then select the `main` branch and `/ (root)` folder.

## Supported browsers

Persistent file connections are designed for current Chromium browsers, particularly Microsoft Edge and Google Chrome. The normal CSV upload fallback remains available in other browsers.

