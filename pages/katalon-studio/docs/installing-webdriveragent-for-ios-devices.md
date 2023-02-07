---
title: "[Mobile] Install WebDriverAgent for iOS devices"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/installing-webdriveragent-for-ios-devices.html
redirect_from:
    - "/display/KD/Installing+WebDriverAgent+for+iOS+devices/"
    - "/display/KD/Installing%20WebDriverAgent%20for%20iOS%20devices/"
    - "/x/TwbR/"
    - "/katalon-studio/docs/installing-webdriveragent-for-ios-devices/"
description:
---

The WebDriverAgent is a WebDriver server used to control iOS devices remotely. It is automatically downloaded with Appium as `appium-webdriveragent`. To learn more about the adoption of WebDriverAgent in Appium, you can refer to the Quamotion document here: [WebDriverAgent vs Appium](https://www.quamotion.mobi/docs/xcuitrunner/webdriver-vs-appium/).

> Requirements:
> * You have enrolled in the Apple Developer Program. To learn more about the Apple Developer Program enrollment, you can refer to this Apple document: [Enrollment](https://developer.apple.com/support/enrollment/).
> * Xcode installation. You can download it from the Apple developer website here: [Xcode](https://developer.apple.com/xcode/).
> * Appium installation. To learn more about installing Appium, you can follow the steps in the Appium document here: [Getting started](http://appium.io/docs/en/about-appium/getting-started/#installing-appium).


In this article, we demonstrate how to install the WebDriverAgent via Katalon built-in tools and manual installation. 

## Install the WebDriverAgent with Katalon built-in tools

From Katalon Studio version 7.2.0 onwards, you can install the WebDriverAgent with Katalon built-in tools. To do so, follow these steps:

1. Download and install a signing certificate and provisioning profile generated from an Apple Developer Account on your development machine. You can manage your signing assets via Xcode. Refer to the following Apple documents for further information: 

   * [Create, export, and delete signing certificates](https://help.apple.com/xcode/mac/current/#/dev154b28f09).
   * [Download manual provisioning profiles](https://help.apple.com/xcode/mac/current/#/deva899b4fe5).

2. Open Katalon Studio and go to **Tools > iOS > Install WebDriverAgent**.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/installing-webdriveragent-for-ios-devices/KS-825-KS-install-WebDriverAgent-built-in-tools.png" width="50%" alt="Install WebDriverAgent via Katalon built-in tools">

3. Katalon Studio detects signing certificates available on your Mac. Choose the certificate generated from an Apple Developer Account.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/installing-webdriveragent-for-ios-devices/KS-8.2.5-detect-certificate-for-WebDriverAgent.png" width="70%" alt="Katalon detects available code signing certificates">

Katalon Studio will build the WebDriverAgent for you.

## Install the WebDriverAgent manually

1. In **Xcode > Preferences > Account**, click *Add* (+) to enter your Apple Developer Account ID and password.

2. To navigate to the location of the WebDriverAgent, open **Terminal**, copy and paste the command line argument below:

   ```groovy
   cd /usr/local/lib/node_modules/appium/node_modules/appium-webdriveragent
   ```

   For Appium version 1.14.2 or older, copy the following command instead: 

   ```groovy
    cd /usr/local/lib/node_modules/appium/node_modules/appium-xcuitest-driver/webdriveragent
   ```

3. After going to the WebDriverAgent location, run the following command to initialize the **WebDriverAgent** project:

   ```groovy
    mkdir -p Resources/WebDriverAgent.bundle
   ```
   
   - For Appium version older than 1.20.0, you also need to run the following script on the same terminal:

      ```groovy
      sh ./Scripts/bootstrap.sh -d
      ```

   > Common issues:
   >
   > * Error code 13: re-run command with sudo: `sudo ./Scripts/bootstrap.sh -d`
   >
   > * Error _Error StackTrace: Cannot find module 'eslint-config-appium': _missing paramter `-d` when running `/Scripts/bootstrap.sh`


4. Open **Finder** and type **appium-webdriveragent** to quickly search for the folder. In the opened folder, double-click the **WebDriverAgent.xcodeproj** file to open it in **Xcode**.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/installing-webdriveragent-for-ios-devices/xcodeproj.png" width=85%>

5. After opening **WebDriverAgent.xcodeproj** file in **Xcode**, you need to build three targets:
   - The **IntergrationApp** target:

      - Select the **IntergrationApp** target. In the **Signing & Capabilities** section, check the **Automatically manage signing** box, then choose the team added in Step 1.

         <a class="pop">
         <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/installing-webdriveragent-for-ios-devices/KS-WEBDRIVERAGENT-Confiugre-IntergrationApp.png" width=85% alt="Configure the IntergrationApp target">
         </a>
         <p style="text-align: center;"><em>Click the image to enlarge it</em></p>

      - On the menu bar, select **Product > Build**.

         <a class="pop">
         <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/installing-webdriveragent-for-ios-devices/KS-WEBDRIVERAGENT-Build-IntergrationApp.png" width=85% alt="Build the IntergrationApp target">
         </a>
         <p style="text-align: center;"><em>Click the image to enlarge it</em></p>

   - The **WebDriverAgentLib** target:
      - Select the **WebDriverAgentLib** target. In the **Signing & Capabilities** section, check the **Automatically manage signing** box, then choose the team added in Step 1.

         <a class="pop">
         <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/installing-webdriveragent-for-ios-devices/KS-WEBDRIVERAGENT-Confiugre-lib.png" width=85% alt="Configure the WebDriverAgentLib target">
         </a>
         <p style="text-align: center;"><em>Click the image to enlarge it</em></p>

      - On the menu bar, select **Product > Build**.

         <a class="pop">
         <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/installing-webdriveragent-for-ios-devices/KS-WEBDRIVERAGENT-Build-lib.png" width=85% alt="Build the WebDriverAgentLib target">
         </a>
         <p style="text-align: center;"><em>Click the image to enlarge it</em></p>

   - The **WebDriverAgentRunner** target:
      
     - Select the **WebDriverAgentRunner** target. In the **Signing & Capabilities** section, check the **Automatically manage signing** box, then choose the team added in Step 1.
         
         <a class="pop">
         <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/installing-webdriveragent-for-ios-devices/KS-WEBDRIVERAGENT-Confiugre-Runner.png" width=85% alt="Configure the WebDriverAgentRunner target">
         </a>
         <p style="text-align: center;"><em>Click the image to enlarge it</em></p>
         
     - On the menu bar, select **Product > Build**.

         <a class="pop">
         <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/installing-webdriveragent-for-ios-devices/KS-WEBDRIVERAGENT-Build-Runner.png" width=85% alt="Build the WebDriverAgentRunner target">
         </a>
         <p style="text-align: center;"><em>Click the image to enlarge it</em></p>
### See also

- [[Mobile]iOS Setup](https://docs.katalon.com/katalon-studio/tutorials/mobile-ios-setup.html#verify-the-ios-application-file)