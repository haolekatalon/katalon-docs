---
title: "Testing Web App on Mobile Browsers"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/running_application_mobile_browsers.html
description: "Learn how to execute Web application testing directly on a mobile device via a sample project on Chrome and Safari browser."
redirect_from:
    - "/katalon-studio/tutorials/running_application_mobile_browsers.html"
---
Katalon Studio supports executing the same test cases on both desktop browsers and mobile browsers. A test case created via recording, either in manual mode or script mode, on a desktop browser with Katalon Studio can be executed on a mobile browser as well. This tutorial will guide you step by step how to do that.

* Understand your web application under test (AUT)
* Create a test case with Katalon Studio
* Execute the test case with mobile browsers

## Requirements

* Katalon Studio: running on both Windows and macOS with a beta Linux support. Visit the [Katalon Studio website](https://www.katalon.com/download) to get the latest version.

* Verify if your computer meets the [System Requirements](http://docs.katalon.com/display/KD/System+Requirements) of Katalon Studio.

* A Katalon account to activate this automation tool. If you don't have one, provide your desired username and password to sign up after launching the app.

* Check out [Quick Start](/katalon-studio/tutorials/web/get-started/quick-start/) to familiarize yourself with Katalon Studio.

Web application testing can be directly executed on a mobile device. To do so, you need to connect your testing devices/emulators to a machine and run test scripts. Make sure Chrome and Safari applications are installed so that test steps can execute properly.

It requires some knowledge of working with OS, Appium, and devices in use. Please refer to our Mobile Setup guide [for Windows](/x/jwbR), or [for macOS](/x/9AXR) for detailed instructions.

## Understand your web application under test (AUT)

When a smartphone is a must-have for everyone, it is required for a web application to accommodate both desktop browsers and mobile browsers.

Often, a desktop UI and a mobile web UI will vary for the same web application since the screen of a desktop is different from that of a phone (in resolution, size, ratio, for example). Thus, a web application with responsive implementation can adapt to various devices, which might cause a problem during the quality assurance period. The same element in different implementation for desktop and mobile may have different locators, and this fact alone can prevent our test cases from executing correctly on mobile browsers.

Do not stress out when your test cases cannot execute properly on mobile browsers as they do on desktop browsers. Automation testing is all about understanding the AUT (Application Under Test) clearly to find a suitable approach. This practice should be a top priority before we want to continue testing our web application.

## Create a test case with Katalon Studio

After understanding your AUT, and you have decided to perform automation testing, let's create a test case with Katalon Studio. Below is the test scenario and how to create the test case in manual mode.

### Scenario: Login

Step 1: Launch Chrome browser on mobile.

Step 2: Enter valid username and password.

Step 3: Click on the login button.

Step 4: Verify login is successful.

### Manual Mode

Step 1: Click on Add from Toolbar and select Web UI Keyword.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/tutorials/running_application_mobile_browsers/web-ui-keyword.png" alt="web UI keyword" width="40%">

Step 2: Select _Open Browser_ and pass the URL in the input field. Call _Wait for Page to Load_ and provide a timeout value in the input field.

Step 3: Add _Wait for Element Visible_ keyword for button object "Make Appointment."

Step 4: Before performing the click action, Verify whether the element is clickable using _Verify Element Clickable_ keyword, pass the object button "Make Appointment."

Step 5: Call _Click_ action to be performed on the "Make Appointment" button.

Step 6: _Wait for Element Visible_ "Login."

Step 7: Add _Verify Element Clickable_ and pass the object as the "Login" button.

Step 8: _Set Text_ for the username as "John Doe".

Step 9:  _Set Text_ in the password as "ThisIsNotAPassword".

Step 10: Add _Click_ action to be performed on the Login button.

Step 11: _Wait for Element_ present of text "Make Appointment".

Step12: Add _Get Text_ keyword to capture the Header "Make Appointment" and store it in a variable called "actual_Header".

Step 13: Use the _Verify Match_ Keyword to verify the actual and expected texts.

Step 14: Close the browser.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/tutorials/running_application_mobile_browsers/830-test-steps.png" alt="test steps" width="100%">

You can also achieve the desired test case by using **Script Mode**.

### Script Mode

```groovy
import static com.kms.katalon.core.testobject.ObjectRepository.findTestObject
import com.kms.katalon.core.model.FailureHandling as FailureHandling
import com.kms.katalon.core.webui.keyword.WebUiBuiltInKeywords as WebUI
 
'Launch Browser'
WebUI.openBrowser('http://demoaut.katalon.com/')
 
'Wait for Page Load'
WebUI.waitForPageLoad(30)
 
'Wait for Element Visible of Button Make Appointment'
WebUI.waitForElementVisible(findTestObject('Browser Application/button_Make Appointment'), 30)
 
'Verify Button Make Appointment is clickable or not'
WebUI.verifyElementClickable(findTestObject('Browser Application/button_Make Appointment'), FailureHandling.STOP_ON_FAILURE)
 
'Click on Button Make Appointment'
WebUI.click(findTestObject('Browser Application/button_Make Appointment'))
 
'Wait for text login Header '
WebUI.waitForElementVisible(findTestObject('Browser Application/text_Login Header'), 30)
 
'Verify text login Header is in visible '
WebUI.verifyElementVisible(findTestObject('Browser Application/text_Login Header'))
 
'Enter username as "John Doe"'
WebUI.setText(findTestObject('Browser Application/txt_UserName'), 'John Doe')
 
'Enter password as "ThisIsNotAPassword"'
WebUI.setText(findTestObject('Browser Application/txt_Password'), 'ThisIsNotAPassword')
 
'Click on Login Button'
WebUI.click(findTestObject('Browser Application/button_Login'))
 
'Wait for Element Present of "Header Make Appointment"'
WebUI.waitForElementPresent(findTestObject('Browser Application/text_Header Make Appointment'), 30)
 
'Get the Header text of Make Appointment and store in "actual_Header" variable'
actual_Header = WebUI.getText(findTestObject('Browser Application/text_Header Make Appointment'))
 
'Verify the actual and Expected text'
WebUI.verifyMatch(actual_Header, 'Make Appointment', false)
 
'Close the Browser'
WebUI.closeBrowser()

```

Do not forget to execute the test case in Katalon Studio again to ensure that it works properly.

## Execute the test case with a mobile browser

Double-check to ensure that the real device is connected, the virtual device loaded, or cloud device connected successfully. From Katalon Studio, select the test case and choose to execute with Android/iOS as follows:

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/tutorials/running_application_mobile_browsers/830-execution.png" alt="execution" width=90%>

It may take a while before the browser can be loaded into the device.

## Troubleshoot common errors

1\. ChromeDriver related error

```groovy
error: No Chromedriver found that can automate Chrome '<chrome_version>'
```

To fix this, you have to download ChromeDriver for Appium manually. You’re recommended to get the version that’s compatible with Chrome on your device. Replace the existing ChromeDriver in Appium Directory with the newly downloaded one.

* macOS: go to **/usr/local/lib/node_modules/appium/node_modules/appium-chromedriver/chromedriver/mac**
* Windows: go to **C:\Users\\<user_name>\AppData\Roaming\npm\node_modules\appium\node_modules\appium-chromedriver\chromedriver\win**

2\. W3C mode related error

```groovy
Caused by: org.openqa.selenium.UnsupportedCommandException: unknown command: Cannot call non W3C standard command while in W3C mode
```

This error is fixed in Katalon Studio version 7.1.0+. Please upgrade for the improvement. Alternatively, you can see a workaround in Katalon forum, click [here](https://forum.katalon.com/t/unable-to-update-chromedriver-on-mac-in-katalon-studio/33958).

## See Also

For further instructions and help, please refer to the [Overview of Documentation](/x/oArR) or [Katalon Forum](https://forum.katalon.com/).
