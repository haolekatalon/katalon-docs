---
title: "How to use Katalon for Azure DevOps"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/azure-devops-extension.html 
description: How to install and setup the Azure DevOps extension.
---
Katalon TestOps Continous Integration (CI) is an easier way to execute Katalon Studio tests remotely or schedule remote Katalon Studio execution. See [Test Planning Overview](https://docs.katalon.com/katalon-analytics/docs/kt-remote-execution.html) for detailed information.

This step-by-step guide shows you how to install the Katalon for Azure DevOps extension and run Katalon projects with Azure DevOps for Web UI testing. 

> Requirements:
>
>  - An active Katalon Runtime Engine license.

## Install the Azure DevOps Extension

To run Katalon projects with Azure DevOps, you first need to install our Katalon for **Azure DevOps** extension from the Visual Studio Market Place. This extension helps download, deploy, and execute Katalon Studio on **Azure DevOps** automatically.

To download and install the **Azure DevOps** extension, perform the following steps:

1. Navigate to [Visual Studio](https://marketplace.visualstudio.com/items?itemName=katalon-llc.katalon&ssr=false#overview).
   
   Click on **Get it Free**.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/azure-devops-extension/K.S.E-8.2.5-azure_devops_extension_download_AzureDevOps.PNG" alt="add task Get it Free" width=100%>

2. From the **Select an Azure DevOps Organization** dropdown, select your organization. Then, click **Install**.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/azure-devops-extension/K.S.E-8.2.5-azure_devops_extension_select_organization.png" alt="add task Select an Azure DevOps Organization" width=100%>

> Notes: 
>
> If you're using Azure DevOps Server, click **Download** and follow instructions as given in the image below.
>
> <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/azure-devops-extension/K.S.E-8.2.5-azure_devops_extension_install_AzureDevOps.PNG" alt="add task Install" width=100%>
>

## Sample Projects

### For Linux

The Azure DevOps extension was tested on Ubuntu 16.0.4 and Ubuntu 18.04. For continuous integration using this version, we recommend our sample scripts on Github: [Azure DevOps sample script](https://github.com/katalon-studio-samples/azure-devops-extension-samples/blob/master/azure-pipelines.yml).

### For Windows

To run UI tests on Azure Pipelines, you might need to adjust the screen resolution (See Microsoft documentation on [Setting screen resolution](https://docs.microsoft.com/en-us/azure/devops/pipelines/test/ui-testing-considerations?view=azure-devops&tabs=mstest#setting-screen-resolution)). 

You can also install the [Screen Resolution Utility](https://marketplace.visualstudio.com/items?itemName=ms-autotest.screen-resolution-utility-task) extension from the Visual Studio Marketplace. 

See our Github examples on how to run a Katalon Studio test: 
>Notes:
>
>The difference between the two examples given below, of "For Windows" and "For Windows resolution", is that VM resolution is 1024 x 768 by default, for which you can run the first script under the "For Windows"example. 
>
>If you need to run your test on a larger resolution, you need to use the second script, that is the example "For Windows resolution".

* For Windows:
[Azure DevOps sample pipeline for windows](https://github.com/duyluonganh/kat-download-file/raw/master/azure-pipelines.yml).

* For Windows resolution:
[Azure DevOps sample pipeline for windows](https://github.com/katalon-studio-samples/azure-devops-extension-samples/raw/master/azure-pipelines-windows-srs.yml).

## Configure the "Execute Katalon Studio Tests" task

Once you have installed the extension, you need to configure the **Execute Katalon Studio Tests** task to complete the integration.

1. Open your Katalon project in Azure DevOps. For more information on how to create a new project in Azure DevOps, see [Microsoft Documentation](https://docs.microsoft.com/en-us/azure/devops/organizations/projects/create-project?view=azure-devops&tabs=preview-page).
   
> Notes:   
>
> If you don't have a project in Azure DevOps, download or clone our demo project from our [GitHub repository](https://github.com/katalon-studio-samples/azure-devops-extension-samples).

2. In your opened project, go to **Repos** > **Files** and click **Set up build**. 

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/azure-devops-extension/K.S.E-8.2.5-azure_devops_extension_set_up_build.png" alt="add task Set up Build" width=100%>

3. In the **Configure your pipeline** page that displays, select **Starter pipeline**.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/azure-devops-extension/K.S.E-8.2.5-azure_devops_extension_starter_pipeline.PNG" alt="add task Starter pipeline" width=70%> 

4. After you click on the Starter pipeline, a new pipeline appears. Click **Show assistant**. 
   
   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/azure-devops-extension/K.S.E-8.2.5-azure_devops_extension_new_pipeline.png" alt="add task Starter pipeline" width=100%> 
   
5. In the **Search tasks** bar of **Task** section, search for **Execute Katalon Studio Tests**.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/azure-devops-extension/K.S.E-8.2.5-azure_devops_execute_katalon_studio_test.png" alt="execute studio tests" width=100%>

6. Fill in the various fields under **Execute Katalon Studio Tests** such as:
   
   - **Download Katalon Studio version**: The version of Katalon Studio that you want to run your test with.
  
   - **Use pre-installed Katalon Studio**: Fill this field only when Katalon Studio cannot be downloaded automatically (often due to network conditions).

      For Example:
   
       - Linux: /var/lib/azureDevops Katalon_Studio_Linux_64-5.10.1 

       - Windows: /var/lib/azureDevops Katalon_Studio_Windows_64-5.10.1

   - **Command Arguments**: Enter the command arguments directly in the text area. You can generate the arguments from Katalon Studio by using the command builder. To learn more, see [Command Syntax](https://docs.katalon.com/katalon-studio/docs/console-mode-execution.html).

      For Example:
      ``` groovy
       -testSuitePath="Test Suites/New Test Suite" -browserType="Chrome" -apiKey=$(katalon_api_key) --config -webui.autoUpdateDrivers=true'
      ```
      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/azure-devops-extension/K.S.E-8.2.5-azure_devops_extension_cmd_arguments.png" alt="enter the arguments" width=100%>   
      
      >Notes:
      >
      > Leave out any irrelevant argument such as `-runmode`. See [Command Arguments in Common Configuration](https://docs.katalon.com/katalon-studio/docs/common-configuration.html#command-arguments) for more details.
      >
   - **X11 DISPLAY (For Linux)**: Leave the **X11 DISPLAY** field blank.

   - **Xvfb-run (For Linux)**: Configure **Xvfb-run** following Ubuntu Manuals on [Xenial xvfb-run](http://manpages.ubuntu.com/manpages/xenial/man1/xvfb-run.1.html). The function still works if you only change the resolution to 1024x768x24 and leave other options as-is.

7. Click **Add** to add these inputs to the pipeline script. The updated pipeline script looks like this:
   
   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/azure-devops-extension/K.S.E-8.2.5-azure_devops_extension_final_test_script.png" alt="updated pipeline script" width=100%>

8.  After everything is set up, click **Run**. If the script is properly configured, it is successfully executed via Azure DevOps. 

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/azure-devops-extension/K.S.E-8.2.5-azure_devops_extension_test_run_1.png" alt="Azure DevOps extension result 1" width=100%>

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/azure-devops-extension/K.S.E-8.2.5-azure_devops_extension_test_run_2.png" alt="Azure DevOps extension result 2" width=100%>
    
## Checking for errors in the pipeline script

Execution of a test script is successful if all the steps in the script are accurate and devoid of any information that does not conform to the requirements of the application that is running the script. Thus, for a proper output to be obtained after running a test script, you have to ensure that all steps in the script are in correct order and devoid of any errors. 

However, if the script fails to execute and you get an error message, perform the following steps:

1. Click **Edit pipeline** to  edit the script.
    
   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/azure-devops-extension/K.S.E-8.2.5-azure_devops_extension_edit_function.png" alt="Azure DevOps Edit pipeline" width=100%>
    
2. The Azure DevOps YAML script displays accordingly. Make the relevant update to the script and click **Save**.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/azure-devops-extension/K.S.E-8.2.5-azure_devops_extension_pipeline_script_displayed.PNG" alt="Azure DevOps YAML script" width=100%>

3. Click **Run** to rerun the script once again.
 
For any troubleshooting issues, go to [troubleshooting in azure devops pipelines](https://docs.microsoft.com/en-us/azure/devops/pipelines/troubleshooting/troubleshooting?view=azure-devops).
