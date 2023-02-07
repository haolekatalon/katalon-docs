---
title: "[WebUI] Smart Wait Function" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/webui-smartwait.html 
description: 
---

One of the most common problems is that Katalon users cannot interact with web page elements, which causes automation tests to fail. Some elements are neither visible nor interactable; the other would receive the operations instead of the intended ones. This issue is because the page hasn't fully loaded or some operations (adding, removing, or modifying elements) haven't finished performing yet.

From Katalon Studio version 7.0.0 onwards, you can enable Smart Wait in project settings to tell the web driver to wait for the web page to become static before performing any operations.

> Requirements:
> * Katalon Studio version 7.0.0 onwards.

You can download the Smart Wait sample project from our Github repository: [Smart Wait sample tests](https://github.com/katalon-studio-samples/smart-wait-example-tests).

## Apply Smart Wait for WebUI testing

> Notes:
> * The Smart Wait function is only available on Chrome and Firefox.
> * From version 8.2.0 onwards, the Smart Wait function is available on Edge Chromium.

Smart Wait is enabled by default in **Project > Settings > Execution > WebUI**. This default configuration will automatically download the Smart Wait extension and apply Smart Wait to all elements in that project.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/execution-settings/KS-PRJ-Smart-wait.png" width="100%" alt="SmartWait settings">

## Apply Smart Wait for remote execution

To apply Smart Wait for remote execution in Chrome, follow these steps:

* In the node machine:

  1. Download a Katalon .zip package. You can download different versions of the Katalon package from our Github repository: [Katalon releases](https://github.com/katalon-studio/katalon-studio/releases). 

  2. Unzip the file and locate the Smart Wait folder. By default, you can find the Smart Wait folder at:

      * For macOS: `<Katalon Studio folder>/Contents/Eclipse/configuration/resources/extensions/Chrome/Smart Wait`.

      * For Windows: `<Katalon Studio folder>\configuration\resources\extensions\Chrome\Smart Wait`.

* In the test runner machine: The test runner machine is where you install Katalon Studio and store the test scripts.

  1. Open Katalon Studio.
  2. Go to **Project > Settings > Desired Capabilities > Remote**, then fill in the following information:

    - Remote Server URL: `http://localhost:port/wd/hub` - the URL of the hub machine.
    - Remote Server Type: Choose **Selenium**.
    - Click **Add** on the command toolbar, then input the following values:

        <table>
      <thead>
        <tr>
          <th colspan="3">Table 1</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Name</td>
          <td>Type</td>
          <td>Value</td>
        </tr>
        <tr>
          <td>browserName</td>
          <td>string</td>
          <td>chrome</td>
        </tr>
        <tr>
          <td>goog:chromeOptions</td>
          <td>Dictionary</td>
          <td>Click <em>More</em> (...). In the pop-up <strong>Dictionary Property Builder</strong> dialog, click <strong>Add</strong>, then input values from Table 2.</td>
        </tr>
      </tbody>
      </table>

      <table>
      <thead>
        <tr>
          <th colspan="3">Table 2</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Name</td>
          <td>Type</td>
          <td>Value</td>
        </tr>
        <tr>
          <td>args</td>
          <td>List</td>
          <td>load-extension=&lt;the absolute path to the Smart Wait folder located in the node machine&gt;</td>
        </tr>
      </tbody>
      </table>

      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/execution-settings/KS-Smart-Wait-set-up-DC-for-remote-execution.png" width="100%" alt="Apply Smart Wait for remote execution in Chrome">

## Temporarily turn off Smart Wait

You can use the `enableSmartWait` and `disableSmartWait` keywords to enable/disable Smart Wait during the test temporarily. Follow these steps:

1. Make sure the **Default Smart Wait** function is enabled in project settings. By enabling this function, Katalon Studio will automatically download and install the Smart Wait extension.

2. Use the `enableSmartWait` or `disableSmartWait` keywords to enable/disable Smart Wait on your target elements.

    In the following example, we first use the `disableSmartWait` keyword to disable Smart Wait at the beginning of the test temporarily.

    Then we use the `enableSmartWait` keyword to enable Smart Wait when setting text on the `Username` object. Smart Wait is enabled until the `disableSmartWait` keyword is applied.

    ```groovy

    WebUI.disableSmartWait()

    WebUI.openBrowser('')

    WebUI.navigateToUrl('https://store.katalon.com/')

    WebUI.maximizeWindow()

    WebUI.click(findTestObject('signin-link'))

    WebUI.enableSmartWait()

    WebUI.setText(findTestObject('username'), 'demo@katalon.com')

    WebUI.setEncryptedText(findTestObject('password'),'3zBGMH+v8QQXwX1AbEAx2g==')

    WebUI.click(findTestObject('signin-button'))

    WebUI.click(findTestObject('menu-dropdown'))

    WebUI.click(findTestObject('dashboard-item'))

    WebUI.click(findTestObject('plugins-item'))

    WebUI.disableSmartWait()

    WebUI.closeBrowser()
    ```
