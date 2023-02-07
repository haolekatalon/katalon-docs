---
title: "TestOps Private Instance integration"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/private-instance-integration.html
redirect_from:
description:
---

If data security is a critical concern for you and your business, testing in a secure environment where sensitive information is isolated can be required.

From Katalon Studio version 8.3.5 onwards, you can privately perform tests and upload test results to TestOps Private Instance from Katalon Studio. 

This article introduces the TestOps Private Instance offering and shows you how to integrate your private instance with Katalon Studio.

## What is TestOps Private Instance?

TestOps Private Instance is a single-tenant cloud architecture where a single software instance and its supporting infrastructure/database serve only one customer, a.k.a a tenant. 

Users can have an isolated TestOps instance with separate application nodes, isolated networking, and database resources. This creates a more secure environment than a multi-tenant architecture where a single software instance and database serve multiple customers. 

To learn more about single-tenant and multi-tenant architectures, you can refer to this Hubspot blog post: [Single vs Multi-Tenant SaaS Architecture](https://blog.hubspot.com/service/single-vs-multi-tenant-saas).

With TestOps Private Instance, you can benefit from:

* Data isolation: This is helpful for users working with sensitive information and strict data storage requirements.

* Data residency: This is helpful for users who must confirm where their data lives or have compliance requirements, for example to be in compliance with General Data Protection Regulation (GDPR).

* Dedicated Katalon application: For users who have a predictable workload and want stronger guarantees in performance, a dedicated instance ensures that they perform tests without being interrupted by maintenance or scaling issues.

* No maintenance: While the dedicated instance offers better data isolation and performance, it is still fully managed by Katalon. This relieves customers from infrastructure management.

## Enable TestOps Private Instance integration in Katalon Studio

> Requirements:
> * Katalon Studio Enterprise version 8.3.5 onwards. To learn more about activating Katalon Studio with TestOps Private Instance, you can refer to this document: [Activate Katalon License](https://docs.katalon.com/katalon-studio/docs/activate-license.html#activate-a-license-with-private-instance).
> * A private instance URL. If you want to learn more about TestOps Private Instance, contact our sales team via business@katalon.com. 

To enable TestOps Private Instance integration in Katalon Studio, follow these steps:

1. Open Katalon Studio.

2. Go to **Project** > **Settings** > **Katalon TestOps**.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/testops-private-instance/KS-8.3.5-Open-TestOps-project-settings.png"  width=80% alt="ks project setting testops integration">

    Alternatively, you can also click the **TestOps** icon from the main toolbar to navigate to the TestOps settings.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/testops-private-instance/KS-8.3.5-TestOps-icon.png"  width=70% alt="TestOps icon">

3. In the **Authentication** section, check **Override Authentication** and input the Private Instance URL, username, and password.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/testops-private-instance/KS-8.3.5-Override-authentication.png" width=70% alt="Enable Override Authentication">

4. Click **Fetch Organizations**.
    
    * Once the connection is successful, Katalon Studio retrieves the organization you belong to.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/testops-private-instance/KS-8.3.5-Successful-override-.png" width=70% alt="Enable Override Authentication">
    
5. In the **Organization** dropdown menu, choose your organization.

6. To upload test results automatically to your Private Instance, in the **Integration** section, select the **Enable Katalon TestOps Integration** checkbox.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/testops-private-instance/KS-8.3.5-Enable-TestOps-integration.png" width=70% alt="Enable TestOps integration">

    * Once the connection is successful, Katalon Studio retrieves all teams and projects from the organization you belong to.

    * Choose your team and project in a dropdown menu of the **Team** and **Project** sections.

    * If you are the owner or admin, you can also click **New Project** to create a new project instead.

    * You can also upload test results manually. Refer to: [Upload test results to Katalon TestOps manually](https://docs.katalon.com/katalon-studio/docs/katalon-analytics-beta-integration.html#upload-test-results-manually).

7. Click **Apply and Close**.

Once TestOps Private Instance integration is enabled, you can execute tests and upload test results to your private instance from Katalon Studio. 

> Notes:
> * When running TestOps Private Instance in console mode, you need to activate the KRE license with Private Instance. To do so, pass the Private Instance URL used for authentication to the `serverURL` parameter. For example: `-serverUrl="https://admin-tenant1.katalon-cloudops.com"`. To learn more about running TestOps Private Instance in console mode, you can refer to this document: [Console Mode Execution](https://docs.katalon.com/katalon-studio/docs/console-mode-execution.html#general-options).

