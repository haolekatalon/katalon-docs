---
title: "Integrate Jenkins Pipeline (Jenkinsfile) with Katalon Studio Docker Image"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/jenkins-pipeline-docker.html 
description: 
---

This tutorial shows you how to integrate Jenkins Pipeline (Jenkinsfile) with Katalon Studio Docker Image. This image contains up-to-date browsers, including Google Chrome, Mozilla Firefox, and Katalon Studio. Hence when running your Katalon Project with Katalon Studio Docker Image, the pre-installed Katalon Studio and Katalon Runtime Engine in your local machine are not required. Docker Image for Katalon Studio is available here at Docker Hub: [katalonstudio/katalon](https://hub.docker.com/r/katalonstudio/katalon/).

> Requirements:
> * Jenkins installed. Follow the instructions in this Jenkins document for installation: [Getting started](https://www.jenkins.io/doc/book/installing/).
> * Docker installed. You can refer to the instructions in the Docker document here: [Get Docker](https://docs.docker.com/get-docker/). 
> * An active Katalon Runtime Engine floating license. To learn more about types of licenses, you can refer to this document: [Types of license](https://docs.katalon.com/katalon-studio/docs/license.html).

## Integrate Jenkins with Docker
### Install plugins
   
1. Install the **Docker** plugin and **Docker Pipeline** plugin. Go to **Manage Jenkins > Manage Plugins > Available tab** and search for the **Docker** plugin and **Docker Pipeline** plugin. 
2. Select the plugin and click **Install without restart**.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/jenkins-docker/plugins.png" alt="plugins" width=70%>
### Add an environment path

> For Windows users, this step is not required. You can now skip to [Upload your Pipline script](https://docs.katalon.com/katalon-studio/docs/jenkins-pipeline-docker.html#upload-your-pipeline-script).

For macOS/Linux, when running builds with Docker from a Jenkinsfile with Pipeline syntax, you need to add an environment path to Jenkins. This `PATH` helps Jenkins point to the correct Docker installation path. Do as follows:

1. To find the correct Docker installation path, open **Terminal**, copy and paste the following command line: `which docker`. The result will tell you where the Docker is. Here, our Docker installation path is: `/usr/local/bin/docker`.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/jenkins-plugin-windows/KS-JENKINS-Docker-installation-path-2.png" alt="Docker installation path" width=70%>

2. Go to **Dashboard > Manage Jenkins > Configure System > Global properties**. Select the **Environment variables** to add a global variable named `PathExtra` with this value: `$PATH:<the correct Docker installation path>`. For our example, the `PathExtra` value is: `$PATH:</usr/local/bin/docker>`.
   
    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/jenkins-plugin-windows/KS-JENKINS-add%20env-path-to-jenkins.png" alt="Add environment path to Jenkins pipline" width=70%>

### Upload your Pipeline script

> Notes: 
> 
> Make sure you have Docker open, with **Docker Plugin** and **Docker Pipeline** activated on Jenkins.

1. In the Jenkins Dashboard, go to **New Item** and create a **Jenkins Pipeline** project.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/jenkins-plugin-windows/create-pipeline.png" width=70%>

2. In the **Definition** dropdown list, you can choose **Pipeline Script** or **Pipeline Script from SCM**, depending on where you store your Jenkinsfile. The **Pipeline Script from SCM** instructs Jenkins to obtain your Pipeline from Source Control Management (SCM), which will be your locally cloned Git repository. To learn more about defining a Pipeline, you can refer to this Jenkins document: [Getting started with Pipeline](https://www.jenkins.io/doc/book/pipeline/getting-started/#defining-a-pipeline-in-scm).

   Here, since we have our Pipeline project stored in Git, we select **Pipeline Script from SCM**.

      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/jenkins-plugin-windows/git.png" width="70%" alt="Choose Pipeline Script from SCM">

3. In the **SCM** field, select **Git**. Enter your repository URL, select branches to build, repository browser, and additional behaviors, if any. You can clone and download the following sample project here: [CI samples](https://github.com/katalon-studio-samples/ci-samples).

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/jenkins-plugin-windows/KS-JENKINS-Add-Git-url-in-pipline-from-SCM.png" width="70%" alt="Enter Git repository url">

4. Specify the Jenkinsfile path from your Git project in the **Script Path** box.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/jenkins-plugin-windows/KS-JENKINS-Add-Jenkinspath-2.png" width="70%" alt="Jenkinsfile path">

   > Notes:
   > 
   > To quickly copy the Jenkinsfile path, go to your Jenkinsfile in your Github repository, click *More* (...), then click **Copy Path**. 
   > 
   > <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/jenkins-plugin-windows/KS-JENKINS-Quickly-go-to-Jenkins-file-in-Git.png" width="70%" alt="Quickly Jenkinsfile path in Git project">

    You can see our sample Jenkinsfile for MacOS/Linux here: [Jenkinsfile](https://github.com/katalon-studio-samples/ci-samples/blob/master/Jenkinsfile). In case you are using Windows, replace the `sh` command in this sample Jenkinsfile with the `bat` command: 

    ``` groovy
    steps {
    bat ''
    }
    ```
    
    For example, we want to run the **TS_RegressionTest** test suite from the **CI samples** project with the Chrome browser in Windows. We adjust the sample Jenkinsfile as follows:

    ``` groovy
    pipeline {
        agent any
        stages {
            stage('Test') {
                steps {
                    dir('/Users/<user_name>/Downloads/ci-samples-master'){
                        bat 'docker run -t --rm -v "$(pwd)":/tmp/project katalonstudio/katalon katalonc.sh -projectPath=/tmp/project -browserType="Chrome" -retry=0 -statusDelay=15 -testSuitePath="Test Suites/TS_RegressionTest" -apiKey=<your-api-key>'
                    }
                }
            }
        }
    ```

    > Notes: 
    >
    > After cloning our sample Jenkinsfile to your repository, customize the below command lines for your purposes:  
    > * `<your-project-folder>`: the direct path to your project folder in the local machine.
    > * `<your_API_Key>`: the API key verifies your credentials. The command-line options of API Key, including `-apiKey=<Your_API_Key>` and `-apikey=<Your_API_Key>` are both accepted. To learn more about API keys, you can refer to this document: [API key](https://docs.katalon.com/katalon-analytics/docs/ka-api-key.html#katalon-api-keys-usage).
    > * From version 7.7.0 onwards, if you belong to more than one Organization subscribing to Runtime Engine licenses, you can choose which Organization validates your license usage with the following command line: `-orgID=<Katalon_OrgID>`.


## Build your project

1.  Click **Save**, then click **Build Now** to run the Jenkinsfile. While the test is being run, if Docker cannot find the `katalonstudio/katalon` image locally, it will automatically pull this image.

      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/jenkins-plugin-windows/KS-JENKINS-Build-now.png" width=60% alt="Build your Jenkins project">

2.  To view the console log, click on your current build on Jenkins and select **Console Output**.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/jenkins-plugin-windows/KS-JENKINS-pipeline-console-output-2.png" width=70% alt="View console output">

    You can also view the console log in Docker during the test.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/jenkins-docker/docker-log.png" alt="docker log" width=70%>

3. To view your report files, you can go to this directory: `<your-project-folder>/Reports` or your third-party integration like Katalon TestOps, Azure DevOps, or qTest. Katalon Studio supports exporting test reports in **HTML**, **CSV**, **PDF**, and **JUnit**.

## See also

* [Integrate Jenkins on Docker hosted in Ubuntu](https://docs.katalon.com/katalon-studio/docs/jenkins-docker-ubuntu.html#install-plugins)