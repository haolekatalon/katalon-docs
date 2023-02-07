---
title: "Upload Test Scripts to a Script Repository" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-analytics/docs/code-repo.html 
description: 
---

> Notes:
>
> Starting Feb 28, 2022 (TestOps February Release), TestOps will:
> * Deprecate the functions *Create Script Repository* and *Update Existing Script Repository* to any project that has not used it before.
> * Retain these functions for any project that has been using them.
>
> Starting Sep 1, 2022, TestOps will:
>
>   *  Deprecate this feature to all projects and associated users - whether they have used it or not.

In Katalon TestOps, you can store your test scripts in a script repository. A script repository helps you manage and organize your test projects better for remote execution.

You can upload your test scripts as a .zip file from your local machine.

## Upload Test Scripts as a .zip file

Follow these steps:
1. Sign in to [Katalon TestOps](https://testops.katalon.io/login) and go to your project. 

    The **Dashboard** page appears.
    
2. Go to **Configurations** > **Script Repositories**.

    The **Script Repositories** page appears.

3. Fill in the following information:
   
     <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/testops-revamp-june-code-repo/create-script-repo-page-2.png" width=100% alt="create script repo page">

    * **Name**: enter a name for your project.
    * **Description**: give detailed information of the project.
    * **Upload**: click **Choose Files** and browse for the compressed project code in your local machine.
    
    > Notes:
    >
    > You can only upload a .zip file.
   
4. Click **Create**.
   
    The uploaded test scripts display in the **Script Repositories** page.

See also:
* [Set up Configurations for Remote Execution](https://docs.katalon.com/katalon-analytics/docs/test-run-config.html).

* [Upload Test Scripts from a Git Repository](https://docs.katalon.com/katalon-analytics/docs/git-test-project.html).

* [Schedule Test Runs](https://docs.katalon.com/katalon-analytics/docs/create-plan.html).

* [Execute Test Runs](https://docs.katalon.com/katalon-analytics/docs/kt-scheduler.html).
 
