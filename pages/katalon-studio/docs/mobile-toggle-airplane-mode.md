---
title: "[Mobile] Toggle Airplane Mode" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/mobile-toggle-airplane-mode.html 
redirect_from:
    - "/display/KD/%5BMobile%5D+Toggle+Airplane+Mode/"
    - "/display/KD/%5BMobile%5D%20Toggle%20Airplane%20Mode/"
    - "/x/XJQY/"
    - "/katalon-studio/docs/mobile-toggle-airplane-mode/"
description: 
---

> Notes:
> * This keyword has been disabled by Android OS since API level 24 (Android 7).
> * To turn airplane mode on/off, you can open the Settings app or swipe down the Control Center, then click/tap the **Airplane Mode** button as a workaround.

## Description  

* Simulate toggling airplane mode on mobile devices.
* Support iOS real devices and Android emulators.

> Notes:
> * On iOS devices, **Access Within Apps** must be enabled. To enable the feature, refer to the following Apple document: [Edit Control Center on your iPhone, iPad, and iPod touch](https://support.apple.com/en-us/HT211812).
## Parameters  

| Param | Param Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | String | Required | \["yes", "on", "true"\] to turn on airplane mode; otherwise, airplane mode is turn off. |
| flowControl | FailureHandling | Optional | Specify failure handling schema to determine whether the execution should be allowed to continue or stop. To learn more about failure handling settings, you can refer to this document: [Failure handling](https://docs.katalon.com/katalon-studio/docs/failure-handling.html#default-failure-handlingbehavior). |

## Example  

You want to turn on airplane mode.

```groovy
import static com.kms.katalon.core.testcase.TestCaseFactory.findTestCase
import static com.kms.katalon.core.testdata.TestDataFactory.findTestData
import static com.kms.katalon.core.testobject.ObjectRepository.findTestObject
import internal.GlobalVariable as GlobalVariable
import com.kms.katalon.core.configuration.RunConfiguration as RunConfiguration
import com.kms.katalon.core.mobile.keyword.MobileBuiltInKeywords as Mobile
import com.kms.katalon.core.util.internal.PathUtil as PathUtil


'Start the application on the currently selected Android device.'
Mobile.startApplication(GlobalVariable.G_AndroidApp, false)

'Turn on airplane mode'
Mobile.toggleAirplaneMode('yes')

'Close application on the currently selected Android device.'
Mobile.closeApplication()
```