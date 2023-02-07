---
title: "Use TestOps Visual Testing" 
sidebar: katalon_studio_docs_sidebar
permalink: /katalon-analytics/docs/ks-visual-testing.html 
redirect_from:
description: This feature helps us compare screenshots between executions.
---

You can compare images captured during test executions with TestOps Visual Testing.

> Requirements:
>
> * You need to subscribe to Katalon TestOps Enterprise plan. To request a trial of Katalon TestOps Enterprise, see [TestOps Trial Plans](https://docs.katalon.com/katalon-analytics/docs/trial-plans.html).
>
> * You have enabled [Katalon Studio Integration](https://docs.katalon.com/katalon-studio/docs/katalon-analytics-beta-integration.html).

## Set up visual testing

Follow these steps:

1. Enable screenshot capture in Katalon Studio. See [Capture Screenshots](https://docs.katalon.com/katalon-studio/docs/capture-screenshots.html).

    > Notes:
    >
    > You can only apply visual testing for screenshots taken as checkpoints.
    >
    > We highly recommend using [[WebUI] Take Screenshot As Checkpoint](https://docs.katalon.com/katalon-studio/docs/webui-take-screenshot-as-checkpoint.html) for new users.

2. Run a Test Suite in Katalon Studio.

    > Notes:
    >
    > If you have enabled Katalon Studio Integration, Katalon Studio automatically uploads Test Results to Katalon TestOps.

3. Sign in to [Katalon TestOps](https://testops.katalon.io/login) and go to your Project.

4. Select **Visual Testing** on the navigation bar.

    The **Visual Test Runs** page appears.

5. Click on the ID of a Test Run.

    The Test Run's **Results** page appears.

6. Select the **Checkpoints** tab.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/testops-revamp-july-visual-testing/checkpoints-page-2.png" width=100% alt="test run #1 checkpoints page">

    You can see the screenshots captured during a test execution.

7. Select one of the screenshots to see the details.  

    > Notes:
    >
    > If you run a Test Suite for the first time, there is no baseline image.

## Configure a baseline image

You can set up a baseline image to compare it with the screenshot of the next Test Run.

Follow these steps:

1. Select a screenshot to see the details.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/testops-revamp-july-visual-testing/id-1-sample-visual-testing.png" width=100% alt="id1 sample visual testing image">

2. Select the *Passed* or *Failed* icon at the top right corner of a screenshot, then close the screenshot.

    An *Unsaved* label now appears on the **Checkpoints** page.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/testops-revamp-july-visual-testing/id-1-unsaved-appears-2.png" width=100% alt="id1 result page with save to baseline button">

3. Go to the **Results** page.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/testops-revamp-july-visual-testing/id-1-save-to-base-line-button-2.png" width=100% alt="id4 highlight unresolved status">

4. Click **Save to baseline**.

> Notes:
>
> If you run a Test Suite for the first time and the Test Suite has passed, the screenshots are automatically marked as *Passed* and there is no **Save to baseline** button. You can open a screenshot and click on the *Failed* icon, then switch back to *Passed* so that the **Save to baseline** button appears.

### View baseline information

To see the baseline images you have saved, go to **Reports** > **Visual Testing** > **Visual Baselines**, then select a screenshot for **Baseline information**.

## Unresolved images

If you run the Test Suite again and the new screenshots of this test execution are different from the baseline images, the status of this Test Run is then marked as *Unresolved*.

To resolve the issues, follow these steps:

1. Click on the ID of the unresolved Test Run.

2. Select and open a screenshot.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/testops-revamp-july-visual-testing/kt-visual-testing-pixel-ui-may2022.png" width=100% alt="mismatch image comparison method box">

    You see a drop-down list in the **Comparison Method** section. The three options include: **Pixel**, **Layout**, **Text Content**.

    > Notes:
    >
    > For detailed information of each comparison method, see: [TestOps Visual Testing](https://docs.katalon.com/katalon-analytics/docs/visual-testing-overview.html#testops-visual-testing).

3. Select one of the three options to start comparing the new screenshot (on the right) with the baseline image (on the left).

    > Notes:
    >
    > **Comparison Method** is enabled only if the status of the screenshot is *mismatched*.

    * If you select **Pixel**, check the **Diffs** between two images (the differences are highlighted in red). See: [Pixel-based comparison](https://docs.katalon.com/katalon-analytics/docs/visual-testing-overview.html#pixel-based-comparison).
    * If you select **Layout**, check the **Identical** and **Distinguishable** and **Missing/New** boxes to see the differences highlighted in green/red/pink color respectively. See: [Layout-based comparison](https://docs.katalon.com/katalon-analytics/docs/visual-testing-overview.html#layout-based-comparison).
    * If you select **Text Content**, check the **Identical** and **Shifted** and **Missing/New** boxes to see the differences highlighted in green/blue/pink color respectively. See: [Content-based comparison](https://docs.katalon.com/katalon-analytics/docs/visual-testing-overview.html#content-based-comparison).

4. Click **Mark as Passed** or **Marked as Failed** to resolve.

    > Notes:
    >
    > * The *Unsaved* label appears whenever you change the status (*Passed* or *Failed*) of a screenshot. If you click **Save to baseline**, the new *Passed* screenshots replace the older baseline images. Katalon TestOps then compares between the new baseline images and screenshots of the next Test Runs.
