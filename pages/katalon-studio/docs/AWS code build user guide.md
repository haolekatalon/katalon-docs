---
title: "Integrate AWS CodeBuild with Katalon Docker Image"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/aws-codebuild-docker-image-integration.html
description: How to integrate AWS CodeBuild with a Katalon Docker Image.
---

> Requirements:
>
> -	*buildspec.yml*: The buildspec file is YAML-formatted and is used to store build commands. You can get this file from our GitHub repository: [Katalon Studio Samples](https://github.com/katalon-studio-samples/ci-samples/blob/master/buildspec.yml). 
>
>    <a class="pop"> 
>
>    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/aws-code-integration-with-docker-image/K.S.E-8.2.5-aws-user-guide-buildspec_file.png" alt="buildspec file with .yml extension" width=80%>  
>    </a>
>
>   <p style="text-align: center;"><em>Click the image to enlarge it.</em></p>
> 
> - Valid Katalon API key:
>You can generate API keys via:
> 
>     - Katalon TestOps
>
>     - Command generator in Katalon Studio.
>
>    Refer to [Generate API keys](https://docs.katalon.com/katalon-analytics/docs/ka-api-key.html#generate-a-katalon-api-key) for more information about API key generation.
>
> - Secret Manager: The *Secret Manager* protects the Katalon API key. To learn more about creating secret keys, refer to the following AWS documentation:
> 
>   -	[Environment Variable AWS codebuild](https://docs.aws.amazon.com/codebuild/latest/APIReference/API_EnvironmentVariable.html).
> 
>   -	[Define environment variables](https://blog.shikisoft.com/define-environment-vars-aws-codebuild-buildspec/).
> 
> - Katalon license: You must have a valid license to run Katalon tests. For more information on licenses, refer to [Katalon license types](https://docs.katalon.com/katalon-studio/docs/license.html#katalon-studio-enterprise).  
>
> * You must be able to integrate your codebuild with *Katalon TestOps* to generate reports. You must also be connected to a repository (for example GitHub) so that you can push your codebuild project. Refer to [TestOps Integration](https://docs.katalon.com/katalon-studio/docs/testops-integration.html#overview) for more details.
> 
## Create an AWS codebuild
To create an AWS codebuild, perform the following steps:

1. Sign in to [Amazon Web Services](http://console.aws.amazon.com), search for AWS CodeBuild, and go to the CodeBuild service.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/aws-code-integration-with-docker-image/K.S.E-8.2.5-aws-user-guide-code-build_search_string.png" alt="search for code build" width=90%>

   The **CodeBuild** page appears.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/aws-code-integration-with-docker-image/K.S.E-8.2.5-aws-user-guide-create_build_project.png" alt="code build page on display" width=100%>

2.	Click **Create build project**.

      Details of the project appear. Fill in the following information.

      **Project Configuration**

      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/aws-code-integration-with-docker-image/K.S.E-8.2.5-aws-user-guide-build_project_configuration.png" alt="project configuration" width=80%>

      **Source**

      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/aws-code-integration-with-docker-image/K.S.E-8.2.5-aws-user-guide-code-build_source_details.png" alt="source details" width=
      80%>

      **Environment**

      > Notes:
      > 
      > When filling the fields in the **Environment** section, ensure that you select the **Privileged** checkbox if you wish to build Docker images or provide your builds with elevated privileges.
      >
      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/aws-code-integration-with-docker-image/K.S.E-8.2.5-license-utilization-dashboard-code_build_environment.png" alt=" environment details" width=70%>

      **Environment (Additional Configuration)**
      
      > Notes:
      >
      > The **Timeout** and **Queued timeout** fields are pre-populated and you can change them as per your requirement.

      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/aws-code-integration-with-docker-image/K.S.E-8.2.5-aws-user-guide-environment_additional_configuration.png" width=70%>

      **Buildspec**

      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/aws-code-integration-with-docker-image/K.S.E-8.2.5-aws-user-guide-use_buildspec_file.png" alt="code buildspec file" width=80%>

1. Click **Create Build Project**.
   
   A **Project created** message displays accordingly. Click **Start build**.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/aws-code-integration-with-docker-image/K.S.E-8.2.5-aws-user-guide-build_project_created.png" alt="code build project created" width=90%>
   
2. Click **Build logs** to monitor the build progress.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/aws-code-integration-with-docker-image/K.S.E-8.2.5-aws-user-guide-build_test_run_logs.png" alt="code build test run logs" width=90%>
   
3. Once the codebuild is complete, you can view its report in *Katalon TestOps*.
   
   <a class="pop">
      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/aws-code-integration-with-docker-image/K.S.E-8.2.5-aws-user-guide-test_run_calendar.png" alt="test run report calendar" width=100%>
   </a>
   
      <p style="text-align: center;"><em>Click the image to enlarge it.</em></p>

   <a class="pop">
      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/aws-code-integration-with-docker-image/K.S.E-8.2.5-aws-user-guide-build_test_run_reports.png" alt="test ops report run details" width=100%>
   </a>
      
      <p style="text-align: center;"><em>Click the image to enlarge it.</em></p>

   ## See Also

   * [View execution reports in TestOps](https://docs.katalon.com/katalon-recorder/docs/monitor-scenario-executions.html).
   * [View Test Case reports with Katalon TestOps](https://docs.katalon.com/katalon-analytics/docs/view-test-cases.html).
   * [[WebUI] Analyze Test Suite Reports and resolve errors](https://docs.katalon.com/katalon-studio/tutorials/webui-view-and-analyze-test-suite-reports.html).