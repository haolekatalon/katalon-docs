---
title: "Generate test scripts for a Progressive Web App using mobile recorder"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/generate-test-scripts-for-progressive-web-app-using-mobile-recorder.html
description: How to generate test scripts for Progressive Web App (PWA) using mobile recorder 
---
A Progressive Web App (PWA) is a modern web application that feels like a web app and works like a native app. It offers rich features such as *Offline mode* and *Push* notifications and creates home screen shortcuts as native apps do. It combines the best features of web apps and native apps. 

This user guide shows you how to record and generate test scripts of a PWA using a mobile recorder. In this example, we wish to record and generate test scripts for the launch of <a href="https://twitter.com/?lang=en">Twitter</a> from the home page of a mobile browser. If you want to test the PWA on a Cloud device, you can use any of the browser testing tools available, such as *Kobiton*, *LambdaTest*, *Browserstack*, etc. We have opted to use BrowserStack as the tool of choice. The use case that you wish to accomplish can be as follows:

- Open the *Chrome* browser on your mobile device.
- Type the <a href="https://twitter.com/?lang=en">Twitter</a> URL in the *Chrome* browser.
- Open the <a href="https://twitter.com/?lang=en">Twitter</a> website.

> Requirements: 
>
> * Android mobile device with a Universal Serial Bus (USB) data cable.
> * Application Under Test (AUT): E.g. <a href="https://twitter.com/?lang=en">Twitter</a> on your mobile.
> * Browserstack AUT ID:  The AUT ID you use based on your Cloud provider.
>
> For more information on how to set up your Android mobile device to test Android applications with **Katalon Studio**, refer to [Android Setup for mobile devices](https://docs.katalon.com/katalon-studio/tutorials/mobile-android-setup.html#set-up-android-tests-on-windows-linux-and-macos).
>
> You can also use an Android Studio Emulator to test Android applications. This eliminates the need for a mobile device physically connected to your system. For more information on how to configure an Android Studio Emulator, refer to [Configure Android Studio Emulator for mobile devices](https://docs.katalon.com/katalon-studio/docs/configure-android-studio.html#configure-android-studio).

To generate test scripts using a mobile recorder, perform the following steps:

## Create and Run your Android test case
For more information on how to create and run your Android test case, refer to [[Mobile] Create and Run Android Test Case](https://docs.katalon.com/katalon-studio/tutorials/mobile-create-android-test-case.html#create-and-run-your-first-android-test-case).

## Configure the remote server settings in Katalon Studio

1. Launch **Katalon Studio** and go to **Project** > **Settings**.
    
    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/generate%20test%20scripts%20using%20mobile%20recorder/K.S.E-8.3.0-generate_test_scripts_configuration_project_settings.png" alt text="project settings" width=70%>

2. The **Project Settings** page appears. Go to **Desired Capabilities** > **Remote**.

    The remote server details display accordingly.

    > Notes:
    > 
    > For more information on configuring your project settings in BrowserStack, refer to [BrowserStack Integration](https://docs.katalon.com/katalon-studio/docs/browserstack-integration.html).

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/generate%20test%20scripts%20using%20mobile%20recorder/K.S.E-8.3.0-generate_test_scripts_configuration_project_settings_remote.png" alt text="project settings remote" width=100%>

    Enter the following remote server information:

    * **Remote server URL**: Enter the URL of your remote server. E.g. http://hub.browserstack.com/wd/hub
    * **Remote server type**: Select  **Appium** in the dropdown list.
    * **Appium driver**: Select **Android Driver** in the dropdown list.

3. Specify whether you want to start the recording with an *Application File* or *Application ID*.
    * Application File: Browse to your tested application (.apk file for Android; .ipa file for iOS)
    * Application ID: Specify the Application ID of your tested application, which is either the package name of an Android app or the bundle identifier of an iOS app.

    > Notes:
    >
    > For more information about how to set up the configuration using *Application File* or *Application ID*, refer to [Introduction to Mobile Recorder](https://docs.katalon.com/katalon-studio/docs/katalon_mobile_recorder_introduction.html#mobile-recorder).
    
## Recording the desired Use Case

1. On the main toolbar of **Katalon Studio**, go to **Action** > **Record** > **Record Mobile**.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/generate%20test%20scripts%20using%20mobile%20recorder/K.S.E-8.3.0-generate_test_scripts_record_mobile_option.png" alt text="record mobile option" width=70%>

2. Click **Start** to begin recording your use case.
   > Notes:
   >
   > * You have to Wait until the AUT launches and the **Device View** and **All Objects** sections are ready for you to interact with the application.        

3. Go to **Device View** > click the *Chrome* icon. 
    
    **Katalon Studio** selects *Chrome* in the **All Objects** section.

    <img src=https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/generate%20test%20scripts%20using%20mobile%20recorder/K.S.E-8.3.0-generate_test_scripts_record_mobile_objects.png alt text="device view" width=100%>
   
4. Once you click on the *Chrome* icon, **Tap** is enabled in the **Available Actions** section. Click **Tap**. The tap action works as follows:

   * The **Device View** displays the new page in the *Chrome* browser.
   * The **Tap** action is added to the list of steps in the **Recorded Actions** section.

5. Click the **Search** field in the *Chrome* browser followed by the **Set text** tab that is enabled. 

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/generate%20test%20scripts%20using%20mobile%20recorder/K.S.E-8.3.0-generate_test_scripts_set_text_tab.png" alt text="set text tab" width=100%> 

6. The **Text Input** dialog box appears. Type the <a href="https://twitter.com/?lang=en">Twitter</a> URL in the dialog box and click **Ok**. 

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/generate%20test%20scripts%20using%20mobile%20recorder/K.S.E-8.3.0-generate_test_scripts_text_input.png" alt text="set text input" width=100%>

7. The <a href="https://twitter.com/?lang=en">Twitter</a> link is added to the **Device View** section and the **Set Text** action is added to the list of steps in the **Recorded Actions** section. 

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/generate%20test%20scripts%20using%20mobile%20recorder/K.S.E-8.3.0-generate_test_scripts_twitter_link_added.png" alt text="twitter link" width=100%>

8. Click the <a href="https://twitter.com/?lang=en">Twitter</a> link in the **Device View** section followed by the **Tap** action that is enabled in the **Available Actions** section. 

    The <a href="https://twitter.com/?lang=en">Twitter</a> home page appears in the **Device View** section and the **Tap** action is added to the **Recorded Actions** section.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/generate%20test%20scripts%20using%20mobile%20recorder/K.S.E-8.3.0-generate_test_scripts_record_twitter_home_page.png" alt text="twitter home page" width=100%>

9. In the **Device View** section > click **Switch to the app** > then click **Capture Object**. Wait until all objects are captured and then click **Tap** in the **Available Actions** section.

    All the actions are recorded, the **Tap** action is added to the **Recorded Actions** section, the mobile device launches the AUT and the current view of the AUT appears. Click **Save Script** to save the test script generated.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/generate%20test%20scripts%20using%20mobile%20recorder/K.S.E-8.3.0-generate_test_scripts_switch_to_app.png" alt text="switch to the app" width=100%> 

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/generate%20test%20scripts%20using%20mobile%20recorder/K.S.E-8.3.0-generate_test_scripts_google_play_signin_screen.png" alt text="google play signin screen" width=100%>

> ## Known issue
>
> An error message appears when you install the Android Studio emulator:
>
> If your system runs on an Advanced Micro Devices (AMD) processor, you might get an *Android Emulator Hypervisor Driver for AMD Processors is not installed* error message.
>
> <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/generate%20test%20scripts%20using%20mobile%20recorder/K.S.E-8.3.0-generate_test_scripts_amd_processor_error.png" alt text="amd procssor error" width=100%>
>
> ## Workaround for "Android Emulator Hypervisor Driver for AMD Processors is not installed" error message
> 
> 1. Go to **Control Panel** > **Programs and Features** > **Windows Features**.
>   
> 2. Clear the **Hyper-V Platform** and **Hyper-V Management Tools** checkboxes, respectively.
>   
>    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/generate%20test%20scripts%20using%20mobile%20recorder/K.S.E-8.3.0-generate_test_scripts_record_clear_hyper-V.png" alt text="switch to the app" width=50%> 
>  
> 3. Reboot the system and access *Bios* > *SVM Mode*.
>
> Notes: 
>
> Depending on the processor, *Secure Virtual Machine (SVM Mode)* is known by different names such as *Virtualization/Inter Virtual Technology*, etc.
>
> In some processors such as *Ryzen*, you can locate *SVM* under  *Configurations* > *SVM Mode* while in others such as *Gigabyte*, you can locate it under *M.I.T* > *SVM Mode*. 
>
> <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/generate%20test%20scripts%20using%20mobile%20recorder/K.S.E-8.3.0-generate_test_scripts_svm_location.png" alt text="svm location" width=50%> 
>
> 4. Change the *SVM Mode* option from *Disabled* to *Enabled*.
>
> 5. Restart your system and proceed with the Android emulator installation.
>
> For more information on how to configure the *Hypervisor Driver* for AMD processors, refer to the [GitHub](https://github.com/search?q=android-emulator-hypervisor-driver) forum.

## See also:

* [Creating a test case using record and playback](https://docs.katalon.com/katalon-studio/videos/create_test_case_record_playback.html).
  
* [Execute and debug a test case](https://docs.katalon.com/katalon-studio/docs/execute-a-test-case-or-a-test-suite.html#execute-a-test-case-or-a-test-suite).
  
