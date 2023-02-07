---
title: "Katalon TestOps 2022 Releases" 
sidebar: katalon_studio_docs_sidebar
permalink: /katalon-analytics/docs/testops-releases-2022.html
description:
---

## Latest Release - May 9th, 2022

### New features
* Implemented the new design for Project Dashboard, adding new dashboards (Productivity and Quality). See: [Introduction to TestOps Dashboard](https://docs.katalon.com/katalon-analytics/docs/dashboard-overview.html).
* Introduced two AI-powered features for visual testing (two additional comparison methods supported by AI engine). See: [Visual Testing Overview](https://docs.katalon.com/katalon-analytics/docs/visual-testing-overview.html).

### Enhancements

* [Integration] Enabled compatibility for Jira version 8.19.1 with Katalon TestOps adds-on.
* [UI/UX] Separated Visual Testing from Reports module. Visual Testing has now become an independent module on TestOps.
* [UI/UX] In the **Test Runs** page, added filters for operating system and browser with their corresponding columns in the **All Test Runs** grid .

## March 29th

### New features

* Introduced the Test Runs Overview module. See: [Test Runs Overview](https://docs.katalon.com/katalon-analytics/docs/test-runs-overview.html).

* Allowed access to a demo site from the organization's dashboard.

* Introduced onboarding tours for key TestOps functionalities.

### Enhancements

* [UI/UX] Disabled the Survey Monkey in the **Test Run Details** page.

* [Script Repository] Required username and PAT input when creating a new Git script repository.

* [UI/UX] Retained the state of previous page in the **Test Suite Details** page.

* [UI/UX] In the **Schedule Test Run** dialog, when choosing **Test Suite** for type:
    * Added **Chrome (headless)** and **Firefox (headless)** options in the **Run with** dropdown list.
    * Removed the currently-selected TestCloud platforms if choosing a different browser from the **Run with** dropdown list.

* [UI/UX] Allowed automatic navigation to the **TestOps** folder in which the new Test Suite has just been created.

* [Administration] Introduced the new license types. See: [Sunsetting plan for node-locked and floating licenses](https://docs.katalon.com/katalon-studio/docs/node-locked-floating-license-sunset-plan.html#change-to-licensing-model).

## February 28th

### New features

* Introduced AWS CodeCommit for test scheduling and test management. Read more: [Upload Test Scripts from a Git Repository](https://docs.katalon.com/katalon-analytics/docs/git-test-project.html#create-git-script-repositories).

### Enhancements

* [Test Suite Management] Enabled test suite deletion.
* [UX/UI] [Test Suite] Allowed script repository to be indicated under loading.
* Disabled .zip script repository uploads for unused projects.
* [UX/UI] [Schedule Test Run] Appended path to test suite name when scheduling test run with Test Suite type.
* [UX/UI] [Schedule Test Run] Made TestCloud as default option in environment selection.

### Bugs
* Resolved security bugs.
  
## January 20th

### New features

* Introduced test suite functionalities for TestOps. Users can create, execute and manage test suites. Read more: [Manage Test Suites](https://docs.katalon.com/katalon-analytics/docs/test-suite-management.html).
* Introduced the design for test suite management. Read more: [Manage Test Suites](https://docs.katalon.com/katalon-analytics/docs/test-suite-management.html).
* Introduced GitLab and Azure Repos integration for test scheduling and test management. Read more: [Upload Test Scripts from a Git Repository](https://docs.katalon.com/katalon-analytics/docs/git-test-project.html).
* Introduce TestCloud Trial Period as a new multi-browser testing environment. Read more: [TestCloud Overview](https://docs.katalon.com/katalon-testcloud/docs/testcloud-overview.html).

### Enhancements

* [Integration] Enabled users to merge existing test results when configuring a new script repository integration.
* [Test Case Management] Enabled the script repository folder refresh in the directory view.
* [UX/UI] Enabled users to resize the test management directory view.
* [UX/UI] Indicated that the script repository is loading.
* [TestCloud] Displayed *Trial* tag for TestCloud environment option when scheduling test runs.
