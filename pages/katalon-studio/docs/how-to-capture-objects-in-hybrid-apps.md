---
title: "Capture elements in hybrid Android apps"
sidebar: katalon_studio_docs_sidebar
permalink: /katalon-studio/docs/capture-elements-in-hybrid-android-apps.html
redirect_from:
description:
---

Katalon Mobile Recorder/Spy utility can detect elements in hybrid app rendered as native app, but cannot as Webview. This tutorial provides a solution to capture Android hybrid mobile elements in WebView with Appium and Chrome Devtools. You can learn more about Android WebView functionalities from the Android developer documentation here: [WebView](https://developer.android.com/reference/android/webkit/WebView).

## Enable WebView debugging for hybrid Android apps

Enable WebView debugging in your Android app. To enable this, set the `setWebContentsDebuggingEnabled` property on the `android.webkit.WebView` element to `true`. You can learn more about configuring WebView for debugging from the Chrome developer documentation here: [Remote debugging WebViews](https://developer.chrome.com/docs/devtools/remote-debugging/webviews/).

## Install Chromedriver for Appium
   
1. Download and install Chromedriver for Appium. You can follow the instruction from the Appium website here: [Chromedriver](http://appium.io/docs/en/writing-running-appium/web/chromedriver/#chromedriverchrome-compatibility). Make sure to download the compatible version with Chrome on your testing devices. 

2. Specify the Chromedriver version in the session. Go to **Project > Settings > Desired Capabilities > Mobile > Android** and add this property:

   <table>
   <thead>
      <tr>
      <th>Name</th>
      <th>Type</th>
      <th>Value</th>
      </tr>
   </thead>
   <tbody>
      <tr>
      <td>chromedriverExecutable(*)</td>
      <td>String</td>
      <td><code>&lt;path-to-your-chromedrive&gt;</code> (**)</td>
      </tr>
   </tbody>
   </table>

   (*) chromedriverExecutable: Support specifying Chromedriver version in session capabilities.

   (**)`<path-to-your-chromedrive>`: full path to the Chromedriver executable downloaded from Step 1. For example: `/Users/katalon.team/node_modules/appium-chromedriver/chromedriver/mac/chromedriver_mac64_v96.0.4664.45`.

   <a class="pop">
   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/capture-objects-in-hybrid-apps/KS-HYBRID-Set-Chrome-executable-path.png" width="70%" alt="Set up Android in Desired Capabilities">
   </a>
   <p style="text-align: center;"><em>Click the image to enlarge it.</em></p>

## Capture elements in hybrid Android apps

1. Create a new test case. Go to **File > New > Test Case**.
2. From the main toolbar in the blank test case page, click **Record Mobile** and select **Android Devices**. 
   To learn more about the Record Mobile utility, you can refer to this document [Record Mobile Utility](https://docs.katalon.com/katalon-studio/docs/record-mobile-utility.html).

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/capture-objects-in-hybrid-apps/Open-mobile-record.png" width="30%" alt="Open Mobile Record">

3. In the pop-up **Mobile Recorder** dialog, specify the information in the **Configuration** section, then click **Start** to begin recording the application under test (AUT).
   
   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/capture-objects-in-hybrid-apps/Start-mobile-record.png" width="50%" alt="Start Mobile Record">

   > Notes:
   > * If your application begins in a WebView, and you don't want to open the AUT in the `NATIVE_APP` context, go to **Project > Settings > Desired Capabilities > Mobile > Android** to set `autoWebview` to `true` in **Desired capabilities**.
   > * With this setting, the AUT automatically enters the `WEBVIEW` context on session start. Skip Step 4,5,6 and move to Step 7 to continue to automate your hybrid app.

4. By default, the Record Utility starts the AUT in the `NATIVE_APP` context. Set to the `WEBVIEW` context by using the `switchToWebView` mobile keyword. More information here: [[Mobile]switchToWebView](https://docs.katalon.com/katalon-studio/docs/mobile-switch-to-web-view.html#example)

   In the main toolbar, click **Add > Mobile keyword**. A new command line appears, then manually add the `switchToWebview` mobile keyword.

   ```groovy
   //to set context to WebView
   Mobile.switchToWebView()
   ```

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/capture-objects-in-hybrid-apps/add-webview-mobile-keyword.001.jpeg" width="70%" alt="Add switch to Webview">

5. Click **Save Script**. An open dialog asks you to save captured objects into the Object Repository of Katalon Studio. Click **OK** to save recorded actions and objects. 

6. In the new test case saved from step 5, do as follows:
   - Switch to the Script tab.
   - Remove command line **Close Application**. 
   - Run the test script.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/capture-objects-in-hybrid-apps/results-after-recording-mobile-test.png" width="70%" alt="Results after recording mobile test">

7. Next, open Chrome browser and navigate to **chrome://inspect/#devices**.
      The **chrome://inspect** page displays:
      - The name of your Android testing device.
      - The version of Chrome that's running on the device, with the version number in parentheses.
      - A list of debug-enabled WebViews on your device. After step 9, you should see the URL of the testing Android application here.
      - Click **Inspect** to open a **Chrome Devtools** instance. Use **Chrome Devtools** to inspect WebView elements.

      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/capture-objects-in-hybrid-apps/chrome-inspect-displays-hybrid-app.png" width="50%" alt="Chrome Inspect displays">


      To learn more about **Chrome Devtools** and its functions, see also [Chrome Devtools](https://developer.chrome.com/docs/devtools/). 

      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/capture-objects-in-hybrid-apps/Chrome-Devtools.png" width="70%" alt="Debug-enabled Webviews in Devtools">


8. Return to Katalon Studio. Create and automate objects in your test with inspected elements from Step 7. To learn more about creating test objects in Webview, you can refer to this document [Web Test Object](https://docs.katalon.com/katalon-studio/docs/manage-web-test-object.html#in-manual-view).
   
      In case you are defining test objects programmatically, you can use the following sample code in the script tab of your test:
      
      ```groovy
      // this is unnecessary if your AUT automatically enters the WEBVIEW context on session start.
      Mobile.switchToWebView()
      // to implement Mobile Driver Factory
      DriverFactory.changeWebDriver(MobileDriverFactory.getDriver())

      // to create a new test object named cdmDetails
      TestObject cdmDetails = new TestObject()
      // to add the object's property inspected from step 10
      cdmDetails.addProperty("id", ConditionType.EQUALS, "119")
      WebUI.setText(cdmDetails, "123")
      ```

      If you wish to stop automating in the `WEBVIEW` context and back to automating the native portion of the app, use the `switchToNative` mobile keyword. More information here: [[Mobile]switchToNative](https://docs.katalon.com/katalon-studio/docs/mobile-switch-to-native.html) mobile keyword.

      ```groovy
      // to switch back to the native mode.
      Mobile.switchToNative()
      ```
## See also

   * [Flutter-based application testing with SetText custom keyword](https://docs.katalon.com/katalon-studio/docs/flutter-based-application-testing.html)
