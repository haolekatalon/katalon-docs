---
title: "[Mobile] Android Setup"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/tutorials/mobile-android-setup.html
redirect_from:
   - "/katalon-studio/docs/mobile-on-windows.html"

description:
---

This article shows you how to set up real Android devices to test Android applications with Katalon Studio.

> If you want to perform Android mobile testing with Android Studio (Emulator), you can refer to this document: [[Mobile] Configure Android Studio (Emulator)](https://docs.katalon.com/katalon-studio/docs/configure-android-studio.html#configure-android-studio).
## Set up Android tests on Windows, Linux, and macOS
   
### On Windows machine

1. Supported environments 
   
   * Appium: 1.12.1 onwards.
   * Android: 6.x onwards (official releases).

2. Download and install the suitable version of Node.js for your system from the Node.js website: [Downloads](https://nodejs.org/en/download/).

   > Notes:
   > * Make sure you install Node.js into a location with full Read/Write permissions.

3. Install Appium version 1.12.1 or newer via NPM. To install the latest Appium version, copy and paste the command-line argument as follows:

   `npm install -g appium`

   > Notes:
   > * We recommend installing the latest Appium version.
   > * Some emulators support Appium directly when installed. If you want to run an application on an emulator, check your emulator settings before installing Appium.

   To learn more about Appium, you can refer to the Appium document here: [Getting started](http://appium.io/docs/en/about-appium/getting-started/#installing-appium).

4. Set up the devices
   
   * Turn on the phone's developer mode. Go to **Settings** > **Developer options**, enable:
   
      - USB debugging – Debug mode when USB is connected.
      - Install via USB – Allow installing apps via USB.
      - USB debugging (Security Setting) – Allow granting permissions and simulating input via USB debugging. 
   
   * Connect your Android phones to your computer via a USB cable.
   * Confirm to accept or trust the device.

5. Install Android SDK
   
   Katalon Studio will automatically detect and ask you to install **Android SDK** if your current machine does not have it.

### On macOS machine

1. Supported environments

   * Appium: 1.12.1 onwards.
   * Android: 6.x onwards.

2. Download and install the suitable version of Node.js for your system from the Node.js website: [Downloads](https://nodejs.org/en/download/).

   > Notes:
   > * Make sure you install Node.js into a location with full Read/Write permissions.

3. Install Appium version 1.12.1 or newer via NPM. To install the latest Appium version, copy and paste the command-line argument as follows:

   `npm install -g appium`

   > Notes:
   > * We recommend installing the latest Appium version.
   > * Some emulators support Appium directly when installed. If you want to run an application on an emulator, check your emulator settings before installing Appium.

   To learn more about Appium, you can refer to the Appium document here: [Getting started](http://appium.io/docs/en/about-appium/getting-started/#installing-appium).
   
4. Set up the devices

   * Turn on developer mode on your Android device. Go to **Settings** > **Developer options**.
   * Connect your Android Phone to your computer via a USB cable. Just confirm if prompted to accept or trust the device.

5. Install Android SDK
   
   Katalon Studio will automatically detect and ask you to install **Android SDK** if your current machine does not have it.

### On Linux machine

1. Supported environments

   * Appium: 1.12.1 onwards.
   * Android: 6.x onwards.

2. Download and install the suitable version of Node.js for your system from the Node.js website: [Downloads](https://nodejs.org/en/download/).

   > Notes:
   > * Make sure you install Node.js into a location with full Read/Write permissions.

3. Install Appium version 1.12.1 or newer via NPM. To install the latest Appium version, copy and paste the command-line argument as follows:

   `npm install -g appium`

   > Notes:
   > * We recommend installing the latest Appium version.
   > * Some emulators support Appium directly when installed. If you want to run an application on an emulator, check your emulator settings before installing Appium.

   * If you see an EACCES error with the Appium installation command, follow the instructions of npm documentation here: [Resolving EACCES permissions errors when installing packages globally](https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally).
   * If you encounter an error where the Java `jar` file can't be found, you might need to add the environment variable: `KATALON_JAVA_HOME= <JRE_location>`. See related discussion on Ask Ubuntu: [How to set JAVA_HOME for Java?](https://askubuntu.com/questions/175514/how-to-set-java-home-for-java?utm_medim=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa)
   * Set the Appium directory manually in **Katalon Studio Preferences**. The default directory should be `/usr/lib/node_modules/appium/`.
   
4. Set up the devices

   * Turn on developer mode on your Android device. Go to **Settings** > **Developer options**.
   * Connect your Android device to your computer via a USB cable. Just confirm if prompted to accept or trust the device.

5. Install Android SDK (Optional)

   Katalon Studio will automatically detect and ask you to install **Android SDK** if your current machine does not have it.
      
## Verify successful Android devices connection

After setting up your environment, to check whether Katalon successfully recognizes your Android devices, you can open a Mobile Testing Sample Project in **File > New sample projects > Sample Android Mobile Tests Project**. 

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/mobile-on-macos/KS-Android-Open--Sample-project.png" width=80% alt="Open Android sample project"> 

On the main toolbar, select the **Android** device in the dropdown list next to **Run**. 

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/execute-mobile-testing-with-emulator/KS-TOOLBAR-Android.png" width=30% alt="Select Android devices">  

You should see the name of your Android device in the pop-up dialog. 

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/mobile-on-macos/device.png" width=50% alt="Katalon recognizes Android devices">

**Next step:**

- [Create your first Android test case](https://docs.katalon.com/katalon-studio/tutorials/mobile-create-android-test-case.html)

## See also:

   * [Troubleshoot automated mobile testing](https://docs.katalon.com/katalon-studio/docs/troubleshooting-automated-mobile-testing.html)
   * Learn more with our Katalon Academy course: [Solve Mobile Testing Challenges with Codeless Solution](https://academy.katalon.com/courses/codeless-solution-mobile-testing/?utm_source=kat_docs&utm_medium=android_setup)
