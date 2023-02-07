---
title: "Integrate Katalon TestOps with Katalon Studio" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/testops-integration.html
redirect_from:
    - "/katalon-studio/docs/execute_tests_periodically_on_remote_machines.html"
    - "/katalon-studio/docs/view-execution-list.html"
---

## Overview

Katalon TestOps is an enterprise-class platform for QA orchestration, test analytics, and advanced reports.

With Katalon TestOps, you can coordinate various activities, cycles, and frameworks in software testing. By doing so, you can ensure software quality at every stage without the need to sacrifice speed or require DevOps expertise.

You can enable TestOps integration in Katalon Studio to upload test results to Katalon TestOps for test management and reports. See: [Upload Test Results to Katalon TestOps from Katalon Studio](https://docs.katalon.com/katalon-studio/docs/katalon-analytics-beta-integration.html#upload-test-results-automatically).

For information on the key modules TestOps offers, see: [TestOps Overview](https://docs.katalon.com/katalon-analytics/docs/overview.html#test-planning).

## Remote execution with TestOps

Katalon TestOps also allows you to:

* [Create a Local Test Environment with an Agent](https://docs.katalon.com/katalon-analytics/docs/agents.html): You can execute tests periodically on remote machines by setting up agents in Katalon TestOps.

* [Upload Test Scripts from a Git Repository](https://docs.katalon.com/katalon-analytics/docs/git-test-project.html):  Retrieve the latest version of your Katalon Studio projects stored in Katalon TestOps or Git.

* [Schedule Test Runs](https://docs.katalon.com/katalon-analytics/docs/create-plan.html#schedule-test-runs): Install and manage multiple versions of Katalon Runtime Engine on your test machines without the need to do so manually.

* [Execute Test Runs manually](https://docs.katalon.com/katalon-analytics/docs/kt-scheduler.html): Execute tests and submit the test results to Katalon TestOps for review.

* [Configure an Agent's Threshold](https://docs.katalon.com/katalon-analytics/docs/load-balancing-agents.html#configure-an-agents-threshold): Keep the number of concurrent executions under a configurable limit.

* [Auto-Distributed Executions](https://docs.katalon.com/katalon-analytics/docs/auto-distributed-execution.html#how-it-works): Katalon TestOps distributes jobs among active Agents to balance workload. This feature is useful especially if you only have a limited number of licenses and want to queue your executions periodically.

* [Requirement Traceability Matrix](https://docs.katalon.com/katalon-analytics/docs/view-traceability-matrix.html): For advanced reports such as traceability matrix report and insights into your testing data, sign in to [Katalon TestOps](https://testops.katalon.io/login) with your Katalon account.

## Enable Katalon TestOps integration

To enable Katalon TestOps integration, follow these steps:

1. Open Katalon Studio.

2. Go to **Project** > **Settings** > **Katalon TestOps**.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/testops-revamp-july-test-uploads-to-kto-from-ks/KS-TESTOPS-Integration.png"  width=100% alt="ks project setting testops integration">

    Alternatively, you can also click the **TestOps** icon from the main toolbar to navigate to the TestOps settings.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/testops-revamp-july-test-uploads-to-kto-from-ks/KS-TESTOPS-icon.png"  width=25% alt="TestOps icon">

3. Tick on the **Enable Katalon TestOps Integration** checkbox.

    Wait for Katalon Studio to connect to Katalon TestOps.
    
    Once the connection is successful, Katalon Studio retrieves all Teams and Projects from the Organization you belong to.
    
4. Choose your Team and Project in a dropdown menu of the **Team** and **Project** sections.

    If you are the Owner or Admin, you can also click **New Project** to create a new Project instead.

5. Click **Apply and Close**.

You've successfully enabled Katalon TestOps integration in Katalon Studio.

Once you have enabled Katalon TestOps integration in Katalon Studio, your Test Results are automatically uploaded to Katalon TestOps every time you run Test Suites in Katalon Studio.
    
<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/testops-revamp-july-test-uploads-to-kto-from-ks/KS-TESTOPS-Upload-results-automatically.png"  width=100% alt="automatic upload of test reports to kto">

## Override authentication

In **Katalon Studio > Project > Settings > Katalon TestOps**, there is an option to override authentication.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/integration-with-katalon-studio/override-authentication.png" alt="override authentication" width="100%">

By default, the **Override authentication** option is disabled, which means the **Server URL** and user credentials to connect with Katalon TestOps are inherited from what has been filled in the **Activation** dialog.

With the **Override authentication** option enabled, you can input a different **Server URL** and user credentials. This information is saved in `<project folder>/settings/internal/com.kms.katalon.integration.analytics.properties`.

You might need to override authentication when you want to integrate Katalon Studio with Katalon TestOps using a TestOps private instance. To learn more about TestOps private instance offering and how to enable your private instance from Katalon Studio, see [TestOps Private Instance integration](https://docs.katalon.com/katalon-studio/docs/private-instance-integration.html).

## Switch Organization in Katalon Studio

You can switch to a different Organization in Katalon Studio by following these steps:

1. Open Katalon Studio and click on the *Profile* icon at the top right corner.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/testops-revamp-july-test-uploads-to-kto-from-ks/KS-TESTOPS-Profile-icon.png" width=100% alt="switch organization in ks">

2. Select **Log out**.

    The **Katalon Studio Activation** box displays.
    
3. Type the new email address and password, then click **Activate**.

You have logged in to a different Organization.

To verify that you have overridden the authentication successfully, click on the *Profile* icon again and select **View Dashboard**.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/testops-revamp-july-test-uploads-to-kto-from-ks/KS-TESTOPS-View-dashboard.png" width=100% alt="view dashboard button in ks">

You will be navigated to the new Organization in Katalon TestOps.

> Learn more about Katalon TestOps with our Katalon Academy course: [Katalon TestOps – Get Better Insights From Your Test Results](https://academy.katalon.com/courses/testops-get-insights/?utm_source=kat_docs&utm_medium=testops_integration).
