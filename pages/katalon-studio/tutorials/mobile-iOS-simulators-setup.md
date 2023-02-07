---
title: "[Mobile] iOS setup (Simulators)"
sidebar: katalon_studio_docs_sidebar
permalink: /katalon-studio/tutorials/mobile-ios-simulators-setup.html
redirect_from:
   - "/katalon-studio/docs/mobile-on-macos.html"
   - "katalon-studio/tutorials/mobile-ios-setup.html"
description:
---
   
This article shows you how to set up Xcode simulators to test iOS applications with Katalon Studio.

To begin with, you need to setup a macOS environment. You can not execute iOS mobile testing in Windows or Linux.

## Part 1: Install Xcode

Install Xcode version 10.2 or newer. You can download Xcode from the App Store or the Apple Developer website: [Xcode](https://developer.apple.com/xcode/).

> Notes:
>
> * Xcode must support the current version of your iOS device.
> * Katalon Studio can only support iOS version 9.0 or above. To learn more about the supported environment in Katalon Studio, you can refer to this document: [Supported environment](https://docs.katalon.com/katalon-studio/docs/supported-environments.html#mobile).

## Part 2: Install Appium and Xcode command-line tools
### Install with built-in tools

From Katalon Studio version 8.3.0 onwards, you can install Appium and Xcode command-line tools (Xcode CLT) via Katalon built-in tools. To do so:

1. Open Katalon Studio and go to **Tools > iOS > Dependencies**. 

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/mobile-recorder-76/iOS/KS-825-Install-dependencies-via-built-in-tools.png" width="50%" alt="Install dependencies via Katalon built-in tools">

2. Katalon will automatically install the latest version of Xcode CLT, Appium, Homebrew, NodeJS, and other iOS dependencies.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/mobile-recorder-76/iOS/KS-825-KS-install-dependencies.png" width="70%" alt="Katalon built-in tools">
### Install manually

1. Install the Xcode command-line tools. You can download the command-line tool compatible with your Xcode version from the Apple Developer website here: [Downloads](https://developer.apple.com/download/all/).

   Alternatively, you can copy and paste the following command-line arguments in this order in the **Terminal** to install the Xcode CLT:

      `xcode-select --install`

      `sudo xcode-select -s /Applications/Xcode.app/Contents/Developer`

2. Download and install Node.js from the Node.js website: [Node.js Downloads](https://nodejs.org/en/download/).

    > Notes:
    > * Make sure you install Node.js into a location where you have full Read/Write permissions.

3. Install Appium version 1.12.1 or newer via NPM. To install the latest Appium version, copy and paste the command-line argument as follows:

    `npm install -g appium `

    > Notes:
    > * We recommend installing the latest Appium version.
    > * If you are using emulators other than Xcode simulators, some emulators come with Appium installed. If you want to run an application on an emulator, check your emulator settings before installing Appium.

    To learn more about Appium, you can refer to the Appium document here: [Getting started](http://appium.io/docs/en/about-appium/getting-started/#installing-appium).
## Part 3: Set up Xcode simulators for mobile testing in Katalon Studio

After installing Xcode, Katalon automatically recognizes Xcode simulators as iOS devices. To check whether Katalon successfully recognizes Xcode simulators, on the main toolbar, select the **iOS** device in the dropdown list next to **Run**.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/mobile-recorder-76/iOS/KS-TOOLBAR-iOS.png" width="30%" alt="Katalon recognizes Xcode simulators">

You should see a list of pre-installed Xcode simulators appearing as iOS devices.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/mobile-recorder-76/iOS/KS-iOS-Katalon-regconizes-simulators.png" width="50%" alt="Katalon recognizes Xcode simulators">

## Part 4: Prepare the iOS application file

To execute mobile testing with Xcode simulators, you need to prepare an `.app` file.

1. Open the `.xcodeproj` project file with Xcode. Here, we open our sample `Coffee Timer.xcodeproj` project file.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/mobile-recorder-76/iOS/open-xcode-file.png" width=70% alt="Open Coffee Timer Xcode project">

2. After opening the project in Xcode, choose one of the iOS simulators to launch the apps.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/iOS-sample-projects/KS-iOS-Choose-simulator-1.png" width=50% alt="Choose the iOS simulators">

3. To build the `.app` file, click **Product > Build**. 
    
    Wait for the build to finish, to find the `app` file, go to `~/Library/Developer/Xcode/DerivedData/{app name}/Build/Products/{scheme}-iphonesimulator/{app name}.app`. In this example, we can find our sample `Coffee Timer.app` file at: `~/Library/Developer/Xcode/DerivedData/Coffee Timer/Build/Products/Debug-iphonesimulator/Coffee Timer.app`.

    > Tips:
    > * To quickly search for the `DerivedData` folder, copy and paste the following path `~/Library/Developer/Xcode/DerivedData` into the **Spotlight**.  

After the above steps, you can now execute mobile testing with Xcode simulators. To learn more about creating and executing iOS mobile testing in Katalon, you can refer to this document: [Create your first iOS test case](https://docs.katalon.com/katalon-studio/tutorials/mobile-create-ios-test-case.html).

## See also:

   * [Troubleshoot automated mobile testing](https://docs.katalon.com/katalon-studio/docs/troubleshooting-automated-mobile-testing.html)
   * Learn more with our Katalon Academy course: [Solve Mobile Testing Challenges with Codeless Solution](https://academy.katalon.com/courses/codeless-solution-mobile-testing/?utm_source=kat_docs&utm_medium=ios_setup)
