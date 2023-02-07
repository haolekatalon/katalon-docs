---
title: "Platform Coverage Dashboard"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-analytics/docs/dashboard-platform-coverage.html 
description: 
---

## Overview

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/overview/kt-dashboard-platform-coverage-ui-may2022.png" width=100% alt="platform coverage dashboard">

The **Platform Coverage** dashboard shows the coverage of test runs or test results in each corresponding operating system and browser. You can filter the profile and specify a period to check the test coverage in your project.

> Notes:
>
> The default period is the last 6 months (compared to the current date).

## Insights

Testing your software/application on different platforms is vital to see if it works accordingly. Hence this dashboard offers you a comprehensive report of all platform performance.

The dashboard offers you the following insights:

* You can understand how many test runs have been executed on each platform based on the size of each dot. Consequently, you know which platform has more or less test executions than the other platforms.
* You can figure out the percentage of failed/passed test runs on each platform based on the color of each dot. Consequently, you know which platform has more or less failed/passed tests than the other platforms.

You then know if your project is going in the right direction through such analytics. Your team could also learn to focus on the prioritized platforms in accordance with the initial plan.

For example, within the default 6-month period and if you select the **By Test Run** option, and the report is represented as follows:

* One green dot in the "Mac OS & Chrome" platform.
* One orange dot in the "Linux & Firefox" platform.
* The size of the green dot is more significant than the orange one.

Then the analytics provides you with the following information:

* Tests are run better (e.g., more *passed* tests and with a consistent result) on Mac OS & Chrome than on Linux & Firefox.

* The quality of test runs on Mac OS & Chrome is better than Linux & Firefox.

* There are more tests on Mac OS & Chrome and they are of a good quality (because the dot is green and bigger in size) while the quality is not so good on Linux & Firefox (because it's orange) and the team should focus on creating more tests and fixing bugs for tests on Linux & Firefox platform.
