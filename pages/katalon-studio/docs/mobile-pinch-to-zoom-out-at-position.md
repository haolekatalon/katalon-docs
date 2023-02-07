---
title: "[Mobile] Pinch to zoom out at position" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/mobile-pinch-to-zoom-out-at-position.html 
redirect_from:
    - "/display/KD/%5BMobile%5D+Pinch+To+Zoom+Out+At+Position/"
    - "/display/KD/%5BMobile%5D%20Pinch%20To%20Zoom%20Out%20At%20Position/"
    - "/x/95IY/"
    - "/katalon-studio/docs/mobile-pinch-to-zoom-out-at-position/"
description: 
---
Description
-----------

Pinch to zoom out at a specific position of the mobile device screen.

Parameters
----------

| Param | Param Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | Number | Required | x position |
| y | Number | Required | y position |
| offset | Number | Required | The offset length to pinch. |
| flowControl | FailureHandling | Optional | Specify [failure handling](https://docs.katalon.com/katalon-studio/docs/failure-handling.html) schema to determine whether the execution should be allowed to continue or stop. |

Example 
--------

You want to pinch to zoom out at position (200,300).

```groovy
import static com.kms.katalon.core.testcase.TestCaseFactory.findTestCase
import static com.kms.katalon.core.testdata.TestDataFactory.findTestData
import static com.kms.katalon.core.testobject.ObjectRepository.findTestObject
import internal.GlobalVariable as GlobalVariable
import com.kms.katalon.core.configuration.RunConfiguration as RunConfiguration
import com.kms.katalon.core.mobile.keyword.MobileBuiltInKeywords as Mobile
import com.kms.katalon.core.util.internal.PathUtil as PathUtil

'Start application on current selected android\'s device'
Mobile.startApplication(GlobalVariable.G_AndroidApp, false)

Mobile.tap(findTestObject('Application/android.widget.TextView - Graphics'), GlobalVariable.G_Timeout)

'Pinch to zoom out at position 200,300'
Mobile.pinchToZoomOutAtPosition(200, 300, 20)

'Close application on current selected android\'s device'
Mobile.closeApplication()
```