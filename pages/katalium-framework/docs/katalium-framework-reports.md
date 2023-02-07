---
title: "Real-time Monitoring and Reporting" 
sidebar: katalon_studio_docs_sidebar
permalink: katalium-framework/docs/katalium-framework-reports.html
description:
---
## TestNG Reports

After execution, TestNG will generate a test-output folder at the root of the project. 

`target/surefire-reports`


## For real-time monitoring and reporting using Katalon Analytics

Go to `src` > `test` > `kata-default.properties`.

Set default values for parameters in the file `kata-default.properties`.

For example, kataProjectId=2, the Project ID will be displayed as https://analytics.katalon.com/team/1/project/2

See real-time monitoring progress of the test execution:

![](https://github.com/katalon-studio/docs-images/raw/master/katalium-framework/docs/katalium-framework-reports/1-test-results.png)

![](https://github.com/katalon-studio/docs-images/raw/master/katalium-framework/docs/katalium-framework-reports/2-test-results.png)


- With Katalium extension in Visual Studio Code, this will be automatically setup.

- With other IDEs, you need to set values for parameters in the files `<user_home>/.katalon/framework.properties` in Katalium Framework.

   KATALON_API_KEY: Enter the API Key. You can generate new API keys at https://analytics.katalon.com. Go to **[Profile](https://analytics.katalon.com/user/profile)** > **Create API Key** > Input key name > Click **Create**.

   KATALON_EMAIL: Enter your Katalon account. You can sign up for a free account at https://www.katalon.com.

   For example:
   
   ```
   KATALON_API_KEY=8077730e-0e09-4b9d-a959-1a62b0a0d6f2
   KATALON_EMAIL=info@katalon.com
   ```

   





