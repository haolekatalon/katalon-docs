---
title: "Continuous Integration with GitLab"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/continuous_integration_gitlab.html
redirect_from:
    - "/katalon-studio/tutorials/continuous_integration_gitlab.html"

description: "This tutorial walks through the steps needed to automatically run your Katalon test suites when you push any change on your Gitlab repository."
---

This tutorial shows you how to integrate your Katalon Studio project with GitLab CI/CD. 

Suppose you are an automation tester using Katalon Studio for testing. In that case, you can integrate your Katalon Studio tests into your GitLab CI/CD and set up your tests to be triggered when there is a new update in your project.

The method for this integration is to run your GitLab CI/CD jobs in a Docker container built from the Katalon Studio Docker image.

Katalon Studio Docker image contains up-to-date browsers, including Google Chrome, Mozilla Firefox, and Katalon Studio. The image is available here at Docker Hub: [katalonstudio/katalon](https://hub.docker.com/r/katalonstudio/katalon/).

> **Requirements**:
>
> * A GitLab account.
> * A Katalon Studio project in GitLab. You can clone or download the sample project on this GitHub repository: [CI Samples](https://github.com/katalon-studio-samples/ci-samples).
> * GitLab Runners configured in your project. To learn more about GitLab Runner, refer to this GitLab document: [Ensure you have runners available](https://docs.gitlab.com/ee/ci/quick_start/#ensure-you-have-runners-available).
> * For self-hosted GitLab Runners, you need to install and run Docker. You can refer to the instructions in the Docker document here: [Get Docker](https://docs.docker.com/get-docker/).
> * An active Katalon Runtime Engine floating license. See: [Types of Licenses](https://docs.katalon.com/katalon-studio/docs/license.html).

## Configure the GitLab project

After setting up the sample GitLab project, you need to configure the following components:

* The `.gitlab-ci.yml` file: A file containing CI/CD configurations.
* Katalon API key variable: A key representing your credentials for Katalon Studio and Katalon Runtime Engine.

### Configure the `.gitlab-ci.yml` file

Open **Pipeline Editor** by selecting **CI/CD** > **Editor**.

The editor displays the `.gitlab-ci.yml` file as follows:

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/tutorials/continuous_integration_gitlab/GitLab-Pipeline-Editor.png" width="100%" alt="GitLab Pipeline Editor .gitlab-ci.yml file">

```yml
# Requirements
# A Katalon Studio project with the content saved in the root repository folder. If the project is under another location, you need to update KATALON_PROJECT_DIR with the corresponding value in the variable section
# An active KRE license
# A valid Katalon API key, which is stored as KATALON_API_KEY in Settings/CI/CD/Variables
image: 'katalonstudio/katalon' # Use the latest version of Katalon Runtime Engine. We can also use other versions of Katalon Runtime Engine by specifying another tag, such as `katalonstudio/katalon:8.1.2` or `katalonstudio/katalon:8.3.0`
services:
  - docker:dind
variables:
  # Specify Katalon Studio project directory. By default, it is stored under the root project folder.
  KATALON_PROJECT_DIR: $CI_PROJECT_DIR
stages:
  - test
test_job:
  stage: test
  # Update your desired katalonc commands. All of katalonc supported arguments can be found in this document https://docs.katalon.com/katalon-studio/docs/console-mode-execution.html
  script:
    - katalonc.sh -projectPath=$KATALON_PROJECT_DIR -apiKey=$KATALON_API_KEY -browserType="Chrome" -retry=0 -statusDelay=20 -testSuitePath="Test Suites/TS_RegressionTest" 
```

You can modify the file with your CI/CD configurations, including:

* `image`: The Katalon Studio Docker image that the job runs in. By default, `katalonstudio/katalon` uses the latest version of Katalon Studio. To use a specific version, input `katalonstudio/katalon:<version_tag>`, for example `katalonstudio/katalon:8.1.2`.

* `KATALON_PROJECT_DIR`: Katalon Studio project directory. By default, it is stored under the root project folder.

* `script`: Your desired `katalonc` commands. All of `katalonc` supported arguments can be found in this document: [Command Syntax](https://docs.katalon.com/katalon-studio/docs/console-mode-execution.html).

To learn more about configuration options, refer to this GitLab document: [.gitlab-ci.yml file](https://docs.gitlab.com/ee/ci/yaml/gitlab_ci_yaml.html).

### Configure the Katalon API Key variable

In the sample `.gitlab-ci.yml` file, we use the `KATALON_API_KEY` to represent the Katalon API key. You need to define this variable and specify its value in the project's settings.

Follow these steps:

1. Go to **Settings** > **CI/CD** and expand the **Variables** section.

2. Select the **Add variable** button and specify these fields:

    * **Key**: `KATALON_API_KEY`.
    * **Value**: \<Your Katalon API key\>. Learn how to generate and view your API key here: [API Keys](https://docs.katalon.com/katalon-analytics/docs/ka-api-key.html).

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/tutorials/continuous_integration_gitlab/GitLab-Add-variable.png" width="100%" alt="GitLab Add variable">

3. Click **Add variable**.
## Test the pipeline

After the configuration, you can start making changes to the project to test the CI/CD pipeline. GitLab CI/CD monitors the changes and runs the job specified in the `.gitlab-ci.yml` file.

To view the jobs running in your project, on the left sidebar, go to **CI/CD** > **Jobs**, and select a job.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/tutorials/continuous_integration_gitlab/GitLab-Select-a-job.png" width="100%" alt="GitLab Select a job">

GitLab displays our job log as follows:

<a class="pop">
<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/tutorials/continuous_integration_gitlab/Gitlab-CI-log.png" width="100%" alt="GitLab job log">
</a>
<p style="text-align: center;"><em>Click the image to enlarge it</em></p>

The job log should display information about the Docker image in use and the output of the configured `katalonc` command.

To view test reports on TestOps, you can enable Katalon TestOps integration in your project. See: [TestOps Integration](https://docs.katalon.com/katalon-studio/docs/testops-integration.html).