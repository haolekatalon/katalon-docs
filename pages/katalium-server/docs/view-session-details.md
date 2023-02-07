---
title: "Sessions monitoring" 
sidebar: katalon_studio_docs_sidebar
permalink: katalium-server/docs/view-session-details.html 
description: Introduce the feature viewing list of sessions and details in Katalium.
---

> This feature is only available in Grid mode.

Katalium Grid Hub will automatically capture screenshots of browsers started by its Grid Node. This will help you monitor on-going sessions and debug test execution errors. All sessions are stored in the directory `<user_home>/katalon-selenium`.

## View all sessions

To see the list of all sessions, go to `http://hub_grid:4444/grid/admin/KatalonConsole/index.html`.

For example:

![](https://github.com/katalon-studio/docs-images/raw/master/katalium-server/docs/view-session-details/1-view-session.png)

## View screenshots of each session

In the list of sessions, select the session you want to view screenshots.

![](https://github.com/katalon-studio/docs-images/raw/master/katalium-server/docs/view-session-details/2-session-details.png)

## Clean up old sessions

Katalium Grid Hub schedules a daily job to clean up sessions older than two months.