---
title: "[Mobile] iOS setup (Real devices)"
sidebar: katalon_studio_docs_sidebar
permalink: /katalon-studio/tutorials/mobile-ios-real-devices-setup.html
redirect_from:
   - "/katalon-studio/docs/mobile-on-macos.html"
   - "/katalon-studio/tutorials/mobile-ios-setup.html"
description:
---
   
This article shows you how to set up real iOS devices to test iOS applications with Katalon Studio.

To begin with, you need to set up a macOS environment. You can not execute iOS mobile testing in Windows or Linux.

## Part 1: Install Xcode

1. Install Xcode version 10.2 or newer. You can download Xcode from the App Store or the Apple Developer website: [Xcode](https://developer.apple.com/xcode/).

   > Notes:
   >
   > * Xcode must support the current version of your iOS device.
   > * Katalon Studio can only support iOS version 9.0 or above. To learn more about the supported environment in Katalon Studio, you can refer to this document: [Supported environment](https://docs.katalon.com/katalon-studio/docs/supported-environments.html#mobile).

## Part 2: Install Appium, Xcode command-line tools, and other iOS dependencies

### Install with built-in tools

From Katalon Studio version 8.3.0 onwards, you can install Appium, Xcode command-line tools (Xcode CLT), and other iOS dependencies via Katalon built-in tools. To do so:

1. Open Katalon Studio and go to **Tools > iOS > Dependencies**. 

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/mobile-recorder-76/iOS/KS-825-Install-dependencies-via-built-in-tools.png" width="50%" alt="Install dependencies via Katalon built-in tools">

2. Katalon will automatically install the latest version of Xcode CLT, Appium, Homebrew, NodeJS, and other iOS dependencies.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/mobile-recorder-76/iOS/KS-825-KS-install-dependencies.png" width="70%" alt="Katalon install dependencies via built-in tools">

### Install manually

1. Install the Xcode command-line tools. You can download the command-line tool compatible with your Xcode version from the Apple Developer website here: [Downloads](https://developer.apple.com/download/all/).

   Alternatively, you can copy and paste the following command-line arguments in this order in the **Terminal** to install the Xcode CLT:

      `xcode-select --install`

      `sudo xcode-select -s /Applications/Xcode.app/Contents/Developer`

2. Download and install Node.js from the Node.js website: [Node.js Downloads](https://nodejs.org/en/download/).

    > Notes:
    > * Make sure you install Node.js into a location where you have full Read/Write permissions.

3. Install Appium version 1.12.1 or newer via NPM. To install the latest Appium version, copy and paste the command-line argument as follows:

    `npm install -g appium`

    > Notes:
    > * We recommend installing the latest Appium version.

   To learn more about Appium, you can refer to the Appium document here: [Getting started](http://appium.io/docs/en/about-appium/getting-started/#installing-appium).

4. Install Homebrew. Homebrew is a package manager that makes it easy to install extra dependencies. To install Homebrew, follow the instructions on the Homebrew website: [Homebrew](https://brew.sh/).

5. After installing Homebrew, you can now use it to install the following dependencies in the **Terminal**:

   - ios-deploy version 1.9.4 or newer. You can learn more about ios-deploy in this Github project: [ios-deploy](https://github.com/ios-control/ios-deploy). To install ios-deploy via Homebrew, copy and paste the command-line argument as below:

      `brew install ios-deploy`

   - usbmuxd version 1.0.10 or newer. You can learn more about usbmuxd in this Github project: [usbmuxd](https://github.com/libimobiledevice/usbmuxd). To install usbmuxd via Homebrew, copy and paste the following command-line arguments in this order:

      `brew install --HEAD usbmuxd`

      `brew unlink usbmuxd`

      `brew link usbmuxd`

   - libimobiledevice version 1.2.0 or newer. You can learn more about libimobiledevice on the libimobiledevice website: [libimobiledevice](https://libimobiledevice.org/). To install libimobiledevice via Homebrew, copy and paste the following command-line arguments in this order:
         
      `brew install --HEAD libimobiledevice`

      `brew unlink libimobiledevice`

      `brew link libimobiledevice`

   - For Appium versions older than 1.20.0, you need to install Carthage. You can learn more about Carthage in this Github project: [Carthage](https://github.com/Carthage/Carthage). To install Carthage via Homebrew, copy and paste the command-line argument below:

      `brew install carthage`

   - For Appium versions older than 1.15.0, you also need to install ios-webkit-debug-proxy. You can learn more about ios-webkit-debug-proxy in this Github project: [ios-webkit-debug-proxy](https://github.com/google/ios-webkit-debug-proxy). To install ios-webkit-debug-proxy via Homebrew, copy and paste the command-line argument as below:

      `brew install ios-webkit-debug-proxy`

## Part 3: Set up real iOS devices for mobile testing in Katalon Studio

> Requirements:
> * You have enrolled in the Apple Developer Program. To learn more about the Apple Developer Program enrollment, you can refer to this Apple document: [Enrollment](https://developer.apple.com/support/enrollment/).

1. Any device for development with Xcode must be listed in the Apple Developer Portal. To learn about listing your device in Apple Developer Portal, you can refer to this wikiHow document: [How to Add a New Device to Your Apple Developer Portal](https://www.wikihow.com/Add-a-New-Device-to-Your-Apple-Developer-Portal).
2. In **Xcode > Preferences > Account**, click *Add* (+) to enter your Apple Developer Account ID and password.
3. Connect your iOS devices to your computer via a USB cable. Confirm to accept or trust the phone.
4. To enable **UI Automation** on the device, navigate to **Settings > Developer**. In the **UI Automation** section, turn on the setting for **Enable UI Automation**.
5. If you want to execute your tests using Safari on iOS (mobile browser), you will need to enable the following settings in **Settings > Safari > Advanced**:

    - JavaScript
    - Web Inspector
    - Remote Automation

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/mobile-recorder-76/iOS/KS-IOS-Safari-Web-Inspector.png" width="40%" alt="Turn on Safari Web Inspector on iOS mobile">

## Part 4: Install the WebDriverAgent

The WebDriverAgent is a WebDriver server used to control iOS devices remotely. To install the WebDriverAgent, you can refer to this document: [Install WebDriverAgent for iOS devices](https://docs.katalon.com/katalon-studio/docs/installing-webdriveragent-for-ios-devices.html#setting-up-the-ios-device).

## Part 5: Distribute your app for testing on registered devices

To distribute your app for testing on registered devices, you need to archive and export an `.ipa` file. Do as follows:
### Prepare your app for distribution

1. Open the project file with Xcode. For example, to open `Coffee Timer.xcodeproj`, from where you store the project > **App** > **Your-First-iOS-App** > **Coffee Timer**. Double-click the `Coffee Timer.xcodeproj` file.

      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/mobile-recorder-76/iOS/open-xcode-file.png" width=70% alt="Open xcodeproj file">

2. After opening the project in Xcode, select a registered iOS device to launch the apps.

      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/mobile-recorder-76/iOS/select-device.png" width=35% alt="Select a registered device">

3. In the **General** tab, set deployment iOS version and select device type in the **Deployment Info** section.

      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/mobile-recorder-76/iOS/deployment.png" width=50% alt="Select deployment info">

4. Switch to the **Signing & Capabilities** tab, check the **Automatically manage signing** box, then choose the team that has your device registered in the Apple Developer Portal. 

   By choosing the **Automatically manage signing** box, Xcode manages code signing assets for you. To learn more about automatic signing, you can refer to this Apple document: [Automatic signing](https://help.apple.com/xcode/mac/current/#/dev80cc24546).

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/mobile-recorder-76/iOS/KS-825-Enable-automatic-signing.png" width=60% alt="Enable automatic signing">

5. To build the `.ipa` file, click **Product > Build**. 

### Create an archive of your app

To archive the `.ipa` file, click **Product > Archive**. If the archive builds successfully, it appears in the Archives organizer.

   > Notes:
   > * You can’t create an archive if you set the run destination to a simulator.

### Export your app using an ad hoc or development provisioning profile

When you export the app, Xcode re-signs the app using the code signing assets that you choose. To learn more about the distribution method, you can refer to this Apple document: [Distribution method](https://help.apple.com/xcode/mac/current/#/dev31de635e5).

1. To open the Archives organizer, choose **Window** > **Organizer** and click **Archives**.
2. Select the archive you want to export, then click **Distribute App** and follow the instructions to get the `.ipa` file. Here, we choose a development provisioning profile to export the `Coffee Timer.ipa` file.

   <a class="pop">
   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/mobile-recorder-76/iOS/export.gif" width=70% alt="Export the .ipa file">
   </a>
   <p style="text-align: center;"><em>Click the gif to enlarge it</em></p>

### Install the app on user devices

To verify the `.ipa` file, follow these steps:

1. Open Xcode, then navigate to **Window > Devices and Simulators**.
2. Choose your device from the **Devices** list.
3. Click *Add* (+) to browse the `.ipa` file.

      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/mobile-on-macos/image2016-8-8-143A313A5.png" width=60% alt="Choose the devices to install the .ipa file">
      
4. Once installed successfully, the application appears in the **Installed Apps** section.  

      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/mobile-on-macos/image2016-8-8-143A313A14.png" width=60% alt="Install the exported .ipa file">

After the above steps, you can now execute mobile testing with real iOS devices. To learn more about creating and executing iOS mobile testing in Katalon, you can refer to this document: [Create your first iOS test case](https://docs.katalon.com/katalon-studio/tutorials/mobile-create-ios-test-case.html).

## See also:

   * [Troubleshoot automated mobile testing](https://docs.katalon.com/katalon-studio/docs/troubleshooting-automated-mobile-testing.html)
   * Learn more with our Katalon Academy course: [Solve Mobile Testing Challenges with Codeless Solution](https://academy.katalon.com/courses/codeless-solution-mobile-testing/?utm_source=kat_docs&utm_medium=ios_setup)
