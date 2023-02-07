---
title: "Google Cloud Build" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/katalon-google-cloud-build.html 
redirect_from:
description: This tutorial shows you how to run a Katalon project with Katalon Docker image on Google Cloud Build.
---

Cloud Build is a service that executes your builds on the Google Cloud Platform (GCP). Cloud Build can import source code from Google Cloud Storage, Cloud Source Repositories, GitHub, or Bitbucket, to continuously build, test, and deploy projects. For more information on Cloud Build, see the Cloud Build documentation: [Cloud Build](https://cloud.google.com/build/docs).

This tutorial shows you how to integrate your Katalon project with Cloud Build.

> **Notes**:
>
> * You can find the sample project in our GitHub repository: [katalon-studio-samples/ci-samples](https://github.com/katalon-studio-samples/ci-samples).

> **Requirements**:
>
> * A valid Katalon API key. See: [Generate API keys](https://docs.katalon.com/katalon-analytics/docs/ka-api-key.html#generate-a-katalon-api-key).
> * A GCP project. See Google Workspace developer documentation: [Create a Google Cloud project](https://developers.google.com/workspace/guides/create-project).
> * Google Cloud Build API enabled for your Google Cloud project. See Google Cloud documentation: [Enabling an API in your Google Cloud project](https://cloud.google.com/endpoints/docs/openapi/enable-api).
> * Secret Manager API enabled for your GCP project. See Google Cloud documentation: [Using secrets from Secret Manager](https://cloud.google.com/build/docs/securing-builds/use-secrets).

## Configure the GCP project

After setting up the GCP project, you need to configure the following components:

* A `cloudbuild.yml` file at the root directory of your repository that contains the build configuration for Cloud Build.
* A GCP secret to store your Katalon API key.

### Configure the `cloudbuild.yml` file

Here in the sample GitHub repository, we have the following `cloudbuild.yml` file:

```yml
steps:
- name: 'docker'
  args: ['pull', 'katalonstudio/katalon']
- name: 'docker'
  entrypoint: 'sh'
  args: ['-c', 'docker run -t --rm -v /workspace:/tmp/project katalonstudio/katalon katalonc.sh -projectPath=/tmp/project -browserType="Chrome" -retry=0 -retryStrategy=immediately -testSuiteCollectionPath="Test Suites/Simple Test Suite Collection" --config -webui.autoUpdateDrivers=true -apiKey=$$KATALON_API_KEY']
  secretEnv: ['KATALON_API_KEY']
availableSecrets:
  secretManager:
  - versionName: projects/$PROJECT_ID/secrets/KATALON_API_KEY/versions/1
    env: 'KATALON_API_KEY'
```

In the build configuration file, there are two build steps:

1. Use a `docker` cloud builder to pull the `katalonstudio/katalon` Docker image from Docker Hub.

    * In the **args** field, you can specify an image version with the syntax `katalonstudio/katalon:<version_tag>`, for example `katalonstudio/katalon:8.1.2`.

2. Use a `docker` cloud builder to run the `katalonstudio/katalon` image as a container and execute the tests stored in the GitHub repository.

    * In the **args** field, you can input your desired `katalonc` commands. All of `katalonc` supported arguments can be found in this document: [Command Syntax](https://docs.katalon.com/katalon-studio/docs/console-mode-execution.html).

    * In the **secretEnv** field, you can input the environment variables for the build. Here we have the `KATALON_API_KEY` variable to specify the use of a secret named `KATALON_API_KEY`.

### Create a GCP secret for Katalon API key

As specified in the build configuration file, the `KATALON_API_KEY` secret represents your Katalon API key. We need to define the secret in our project.

For detailed instructions on creating a GCP secret, refer to this Google Cloud guide: [Creating and accessing secrets](https://cloud.google.com/secret-manager/docs/creating-and-accessing-secrets).

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/google-cloud-build-integration/GCP-Secret-key.png" alt="Google Cloud Platform secret manager" width="100%"> 



## Create and test your build trigger

A Cloud Build trigger automatically starts a build whenever you make changes to your source code. You need to connect Cloud Build to the sample GitHub repository and then create a trigger that automatically monitors changes and builds code.

For detailed instructions on connecting to repositories and building triggers, refer to this guide: [Creating and managing build triggers](https://cloud.google.com/build/docs/automating-builds/create-manage-triggers).

### Create a trigger

In our example, a trigger is created to build the code automatically whenever a **Push to branch** event occurs.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/google-cloud-build-integration/GCP-Created-trigger.png" alt="Google Cloud Platform trigger created" width="100%"> 

### Test the trigger

To test the trigger, you can start the build manually by clicking **Run** on the trigger.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/google-cloud-build-integration/GCP-Run-trigger.png" alt="Google Cloud Platform run trigger" width="100%">

### View build results

To view the build results, go to the **History** tab and select the latest build.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/google-cloud-build-integration/GCP-History-tab.png" alt="Google Cloud Platform history tab" width="100%">

The build details are shown as follows:

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/google-cloud-build-integration/GCP-Build-details.png" alt="Google Cloud Platform build details" width="100%">

We can see that the code build includes two steps: pulling the Docker image and executing the tests in a container.

To view test reports in TestOps, you can enable Katalon TestOps integration in your project. See: [TestOps Integration](https://docs.katalon.com/katalon-studio/docs/testops-integration.html).