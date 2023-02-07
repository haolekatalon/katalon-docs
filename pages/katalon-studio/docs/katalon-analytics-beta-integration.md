---
title: "Upload Test Results to Katalon TestOps from Katalon Studio" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/katalon-analytics-beta-integration.html
redirect_from:
    - "/display/KD/Katalon+Analytics+%28Beta%29+Integration/"
    - "/display/KD/Katalon%20Analytics%20%28Beta%29%20Integration/"
    - "/x/KRhO/"
    - "/display/KA/Integration+with+Katalon+Studio/"
    - "/display/KA/Integration%20with%20Katalon%20Studio/"
    - "/katalon-analytics/docs/ka-integration-katalon-studio/"
    - "/katalon-analytics/docs/ka-integration-katalon-studio.html"
    - "/katalon-analytics/docs/view-reports/"
    - "/x/mw3R/"
    - "/katalon-analytics/docs/integration-with-katalon-studio.html"
    - "/katalon-analytics/docs/upload-reports-overview.html"
    - "/katalon-analytics/docs/project-management-import-KS.html"
    - "/katalon-analytics/docs/ks_upload_project_kt.html"
---

> Notes:
>
> * Katalon Studio version 7.0 onwards supports video capture of Test Results when uploading them to Katalon TestOps.

From Katalon Studio, you can view the execution summary, then upload test results to Katalon TestOps manually or automatically.

## View execution summary in Katalon Studio

> Requirements:
>
> * Katalon Studio version 7.6.2 onwards.
> * You have enabled TestOps integration in Katalon Studio.
> * You have executed at least one test suite in Katalon Studio.

Follow these steps:

1. Open Katalon Studio.

2. On the **Tests Explorer** sidebar, go to **TestOps** > **Executions**.

    You can view a summary of your test executions here.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/view-execution-list/execution-list.png" width=100% alt="execution list">

    > Notes:
    >
    > You can click on the *Reload* icon (next to **View all executions** in the top right corner) to view the latest updates.

## Upload test results automatically

To automatically upload test results to Katalon TestOps, you need to enable TestOps integration in Katalon Studio. Follow the steps in this guide: [Enable Katalon TestOps integration](https://docs.katalon.com/katalon-studio/docs/testops-integration.html#enable-katalon-testops-integration).

Once you have enabled Katalon TestOps integration in Katalon Studio, your Test Results are automatically uploaded to Katalon TestOps every time you run Test Suites in Katalon Studio.
    
<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/testops-revamp-july-test-uploads-to-kto-from-ks/KS-TESTOPS-Upload-results-automatically.png"  width=100% alt="automatic upload of test reports to kto">

## Upload test results manually

You can also upload test results manually by following these steps:

1. Open Katalon Studio and go to the project you are working on.

2. Go to **Test Suites** or **Test Suite Collection** and choose your Test Suite.

    Select the **Result** tab.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/testops-revamp-july-test-uploads-to-kto-from-ks/KS-TESTOPS-Upload-result-manually.png" width=100% alt="upload manually from ks to testops">

3. Click on the **Katalon TestOps** tab at the top right corner and select **Upload**.

4. Choose the Team and Project you want to upload test results to.

5. Click **Upload**.

You have uploaded test results manually to Katalon Testops.
