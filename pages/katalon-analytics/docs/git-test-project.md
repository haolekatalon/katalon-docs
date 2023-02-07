---
title: "Upload Test Scripts from a Git Repository" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-analytics/docs/git-test-project.html 
description: 
---

You can create a Git script repository in Katalon TestOps. Katalon TestOps can then upload test scripts automatically from a Git repository. This allows you to store your test scripts in your Git accounts and execute them in Katalon TestOps.

Katalon TestOps allows AWS CodeCommit, Azure Repos, Bitbucket, GitHub and GitLab integration for Git repositories.

> Requirements:
>
> * An existing [Azure Repos](https://azure.microsoft.com/en-us/services/devops/repos/)/ [Bitbucket](https://bitbucket.org/product)/ [GitHub](https://github.com)/ [GitLab](https://about.gitlab.com/install/)/ [AWS CodeCommit](https://docs.aws.amazon.com/codecommit/index.html) account.

## Create Git Script Repositories

Follow these steps:

1. Sign in to [Katalon TestOps]( https://testops.katalon.io/login) and go to the project you want to create a Git repository for.

   Go to **Configurations** > **Script Repositories**.
   
   The **Script Repositories** page appears as below.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/testops-revamp-june-git-test-project/script-repo-screen-in-testops-config-new-2.png" width=100% alt="script repo page">

2. Click **Create Git Script Repository**.

3. Fill in the required information.
   >
   > Notes: 
   >
   > When you select the **AWS CodeCommit** option from the dropdown, the **Access Key ID** and **Secret Access Key** fields are enabled.
   >
   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/testops-revamp-june-git-test-project/K.S.E-8.2.5-script-repo-page-after-creating-git-repository.png" width=100% alt="create script repo page">

   * **Source Type**:  choose your Git script repository source type (**Azure Repos**/ **Bitbucket**/ **GitHub**/ **GitLab**/**AWS CodeCommit**).
   * **Repository URL**: enter the URL of your Git script repository.
   * **Username**: enter your Azure Repos/ Bitbucket/ GitHub/ GitLab username.
   * **Personal Access Token**: enter your Personal Access Token (PAT).
   * **Access Key ID**: enter your Access Key ID.
   * **Secret Access Key**: enter your Secret Access Key.

> Notes:
>
> To get information on your repository URL and username, see the following documentation:
>  * [Azure Repos Git Documentation](https://docs.microsoft.com/en-us/azure/devops/repos/git/?view=azure-devops).
>  * [Bitbucket Documentation](https://confluence.atlassian.com/bitbucketserver/bitbucket-data-center-and-server-documentation-776639749.html).
>  * [GitHub Documentation](https://docs.github.com/en).
>  * [GitLab Documentation](https://docs.gitlab.com/ee/).
>  * [AWS CodeCommit Documentation](https://docs.aws.amazon.com/codecommit/latest/userguide/setting-up-gc.html).
>
> To get information on your repository URL (HTTPS), refer to “Step 4“ of [Setup for HTTPS users using Git credentials](https://docs.aws.amazon.com/codecommit/latest/userguide/setting-up-gc.html).
>
>To get information on username and PAT (password), refer to “Step 3“ of [Setup for HTTPS users using Git credentials](https://docs.aws.amazon.com/codecommit/latest/userguide/setting-up-gc.html).
>
>To get the information on Access Key ID and Secret Access Key, see  [Managing  Access Keys for IAM Users](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html).
> 
>
> To create a PAT, see the following guides:
> * For AWS CodeCommit, refer to Step 4 of [AWS CodeCommit Documentation](https://docs.aws.amazon.com/codecommit/latest/userguide/setting-up-gc.html).
> * For Azure Repos, see: [Use personal access tokens](https://docs.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate?view=azure-devops&tabs=preview-page).
>  * For Bitbucket, see: [HTTP access tokens](https://confluence.atlassian.com/bitbucketserver/personal-access-tokens-939515499.html).
>  * For GitHub, see: [Create a Personal Access Token](https://help.github.com/en/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line).
>     * Follow instructions and make sure you choose **repo** in the **Select scopes** section in the **New personal access token** page.
> 
>         <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-analytics/docs/testops-revamp-june-git-test-project/new-personal-access-toke-page-git.png" width=100%>
>         
>  * For GitLab, see: [Create a personal access token](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html#create-a-personal-access-token).

1. Click **Connect**.

   The following sections appear:

   * **Branch**: choose a branch.
   * **Name**: enter your project name.

2. Click **Create**.

You have enabled Azure Repos/ Bitbucket/ GitHub/ GitLab integration and created a new Git script repository in Katalon TestOps.

Next step:
* [Schedule Test Runs](https://docs.katalon.com/katalon-analytics/docs/create-plan.html).
