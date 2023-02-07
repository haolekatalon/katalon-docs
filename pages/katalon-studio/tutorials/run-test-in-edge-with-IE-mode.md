---
title: "Execute test in Internet Explorer (IE) mode in Microsoft Edge" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/run-test-in-edge-with-IE-mode.html
description: "This tutorial shows you a workaround to run test cases with Edge browser in IE mode."
---

As the Internet Explorer desktop application is determined to go out of support on June 15, 2022, Microsoft introduces IE mode in Microsoft Edge for organizations that still need Internet Explorer 11 for backward compatibility for legacy websites or apps. To learn more about IE mode, refer to this Microsoft document: [What is Internet Explorer (IE) mode?](https://docs.microsoft.com/en-us/deployedge/edge-ie-mode)

This tutorial shows you how to use Katalon Studio to run test cases in IE mode in Microsoft Edge.

In our example, we use a custom keyword called `openIEModeEdgeBrowser` to open Microsoft Edge in IE mode. To learn more about custom keywords in Katalon Studio, refer to this document: [Introduction to Custom Keywords](https://docs.katalon.com/katalon-studio/docs/introduction-to-custom-keywords.html).

You can find the sample project with the custom keyword in this GitHub repository: [Open IE Mode in Edge Chromium](https://github.com/ducnguyen505/Open-IE-Mode-Edge-Sample-Project).

> **Known Limitation**:
>
> * You can execute tests in Internet Explorer (IE) mode in Microsoft Edge, but you cannot record new tests in IE mode in Microsoft Edge.

## Configure Internet Options settings

* On Windows 10, follow the steps in this guide: [Internet Explorer Configurations](https://docs.katalon.com/katalon-studio/docs/internet-explorer-configurations.html).

* On Windows 11, follow these steps:
    1. Open **Control Panel** and go to **Network and Internet** > **Internet Options**.

    2. In the **Internet Properties** dialog, select the **Security** tab and choose **Local intranet**.
    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/tutorials/run-test-in-edge-with-IE-mode/Internet-Properties-dialog.png" alt="Create a new Keyword Package">

    3. Click on the **Sites** button and enable **Automatically detect intranet network**.
    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/tutorials/run-test-in-edge-with-IE-mode/Local-intranet-selected.png" alt="Create a new Keyword Package">

    4. Click **OK**.

## Create the openIEModeEdgeBrowser custom keyword

1. Go to **Tests Explorer** > **Keywords**, and create a new keyword package.

    Here we name the package `com.example`.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/tutorials/run-test-in-edge-with-IE-mode/KS-Create-new-keyword-package.png" alt="Create a new Keyword Package">

2. Right-click on the newly created package and create a new keyword class.

    We name the class `openIEModeEdgeBrowser`.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/tutorials/run-test-in-edge-with-IE-mode/KS-Create-new-keyword-class.png" alt="Create a new Keyword class">

    In the `openIEModeEdgeBrowser.groovy` file, copy and paste the following script and save it.

    ```groovy
    package com.example
    import static com.kms.katalon.core.checkpoint.CheckpointFactory.findCheckpoint
    import static com.kms.katalon.core.testcase.TestCaseFactory.findTestCase
    import static com.kms.katalon.core.testdata.TestDataFactory.findTestData
    import static com.kms.katalon.core.testobject.ObjectRepository.findTestObject

    import com.kms.katalon.core.annotation.Keyword
    import com.kms.katalon.core.checkpoint.Checkpoint
    import com.kms.katalon.core.checkpoint.CheckpointFactory
    import com.kms.katalon.core.mobile.keyword.MobileBuiltInKeywords
    import com.kms.katalon.core.model.FailureHandling
    import com.kms.katalon.core.testcase.TestCase
    import com.kms.katalon.core.testcase.TestCaseFactory
    import com.kms.katalon.core.testdata.TestData
    import com.kms.katalon.core.testdata.TestDataFactory
    import com.kms.katalon.core.testobject.ObjectRepository
    import com.kms.katalon.core.testobject.TestObject
    import com.kms.katalon.core.webservice.keyword.WSBuiltInKeywords
    import com.kms.katalon.core.webui.keyword.WebUiBuiltInKeywords

    import internal.GlobalVariable

    import org.openqa.selenium.WebElement
    import org.openqa.selenium.ie.InternetExplorerDriver
    import org.openqa.selenium.ie.InternetExplorerOptions
    import org.openqa.selenium.WebDriver
    import org.openqa.selenium.By

    import com.kms.katalon.core.mobile.keyword.internal.MobileDriverFactory
    import com.kms.katalon.core.webui.driver.DriverFactory

    import com.kms.katalon.core.testobject.RequestObject
    import com.kms.katalon.core.testobject.ResponseObject
    import com.kms.katalon.core.testobject.ConditionType
    import com.kms.katalon.core.testobject.TestObjectProperty

    import com.kms.katalon.core.mobile.helper.MobileElementCommonHelper
    import com.kms.katalon.core.util.KeywordUtil

    import com.kms.katalon.core.webui.exception.WebElementNotFoundException


    class openIEModeEdgeBrowser {
        /**
        * Open browser
        */
        @Keyword
        def openBrowser(String url) {
            System.setProperty("webdriver.ie.driver", DriverFactory.getIEDriverPath());
            InternetExplorerOptions edgeIe11Options = new InternetExplorerOptions();
            Map<String, Object> ops = (Map<String, Object>) edgeIe11Options.getCapability("se:ieOptions");
            ops.put("ie.edgechromium", true);
            ops.put("ie.edgepath", "C:\\Program Files (x86)\\Microsoft\\Edge\\Application\\msedge.exe");
            edgeIe11Options.setCapability("ignoreProtectedModeSettings", true);
            edgeIe11Options.setCapability("ignoreZoomSetting", true);
            WebDriver driver = new InternetExplorerDriver(edgeIe11Options);
            driver.get(url)
            DriverFactory.changeWebDriver(driver)
        }
    }    
    ```
## Use the custom keyword to execute test cases in IE mode

1. In Katalon Studio, create a test case.

2. Modify the test case. Open the test case and use the custom keyword as the first test step to open Microsoft Edge in IE mode.

    For example, we use the custom keyword at the beginning of the test case.

    In **Manual** view:
    
    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/tutorials/run-test-in-edge-with-IE-mode/KS-Test-case-manual-view.png" alt="Use keyword in test case">

    In **Script** view:

    ```groovy
    // Use the custom keyword and URL defined as global variable to open the site in Edge, with IE mode
    CustomKeywords.'com.example.openIEModeEdgeBrowser.openBrowser'(GlobalVariable.G_SiteURL)
    ```

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/tutorials/run-test-in-edge-with-IE-mode/KS-Use-custom-keyword-in-test-case.png" alt="Use keyword in test case">
    

3. Save your test case, then select the **IE** option to run the test.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/tutorials/run-test-in-edge-with-IE-mode/KS-Run-dropdown-IE.png" alt="Run dropdown">

    Katalon Studio should open a Microsoft Edge browser session in IE mode.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/tutorials/run-test-in-edge-with-IE-mode/AUT-opened-in-IE-mode.png" alt="Microsoft Edge browser session opened">

4. Verify the results in **Log Viewer**.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/tutorials/run-test-in-edge-with-IE-mode/KS-Log-View-results.png" alt="Use keyword in test case">