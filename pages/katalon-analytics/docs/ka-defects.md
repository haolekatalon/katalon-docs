---
title: "Defects" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-analytics/docs/ka-defects.html 
redirect_from: /katalon-analytics/docs/kt-jira-issue.html
description: 
---

If a Test Run fails, you can link its Test Result to Jira issues, such as Jira Bugs. You can then view the Test Result of that Test Run in Jira to investigate the Defects.

> Requirements:
>
> * You have installed the [Jira App](https://marketplace.atlassian.com/apps/1217501/katalon-bdd-test-automation-for-jira).
>
> * You have configured Jira integration. See: [Jira Settings](https://docs.katalon.com/katalon-analytics/docs/kt-jira-config.html).

## Link Test Results to Jira

To link a Test Result to a Jira Bug, follow these steps:

1. Sign in to [Katalon TestOps](https://testops.katalon.io/login) and go to your Project.

2. Go to **Reports** > **Test Runs**.

3. Select a failed Test Run by clicking on its ID, then click on the **Test Results** tab.

    The **Test Results** page appears as below.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/testops-revamp-july-ka-defects/test-result-page-defect-icon-2.png"  width=100% alt="test results page with defects box">

3. Mouse over the Test Result you want to link to a Jira Bug. The *Bug* icon appears in the **Links** column.

4. Click on the *Bug* icon.

    The screen appears as below.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/testops-revamp-july-ka-defects/jira-defect-screen-appears-2.png"  width=100% alt="defect screen">

5. Search for the Jira issue in the **Jira Defects** section, then click on the *Link* icon.

You have linked a Test Result to a Jira Bug.

### Quick Tips

You can also install the Katalon Integration Plugin in your Chrome browser. This Plugin allows you to navigate directly to Jira to create a new Jira issue. It then automatically links the Jira issue back to the Test Result you have selected.

Follow these steps:

1. Download [Katalon Integration Plugin](https://chrome.google.com/webstore/detail/katalon-integration/cechonbcopffiimhnkgghckbgipciedg).

    > Notes:
    >
    > The download is only available on the Chrome browser.

2. Enable Katalon Plugin in Chrome Extensions.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/testops-revamp-july-ka-defects/chrome-extension-page-katalon-plugin.png"  width=100% alt="chrome extension page">
    
3. Check the **Jira Defects** section in Katalon TestOps again.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/testops-revamp-july-ka-defects/create-icon-enabled-in-jira-defect-2.png"  width=100% alt="create icon enabled in testops">

    After completing the installation, the *Create* icon is enabled.

4. Click on the **Create** icon to switch directly to Jira, then create a new Jira issue.

    The new Jira issue is automatically linked to the Test Result you have selected.
     
> Notes:
>
> Once you have enabled Katalon Plugin, you can see the *Plugin* icon in the corner of a Jira issue.
> <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/testops-revamp-july-ka-defects/link-test-run-to-kat102defect-blurname.png"  width=100% alt="plugin icon floating in jira">
>
> You can always click on the *Plugin* icon to quickly switch back to Katalon TestOps.

## View linked Test Runs in Jira

1. Go to the Jira issue you have linked the Test Results to.

2. Click on the **Linked Test Runs** section to see all Test Results of the linked Test Runs.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/testops-revamp-july-ka-defects/jira-link-test-run-section-plugin.png"  width=100% alt="jira linked test runs section">

## View Defects in Katalon TestOps

Select a Test Run by clicking on its ID, then select the **Defects** tab on the Test Run page.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/testops-revamp-july-ka-defects/defects-of-a-test-run-id-2.png" width=100% alt="test run id's defects tab">

You can view all Jira issues associated with the Defects of a Test Run here.

To see all other Defects, go to **Reports** > **Defects**.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/testops-revamp-july-ka-defects/all-defects-page-2.png" width=100% alt="all defects page">
