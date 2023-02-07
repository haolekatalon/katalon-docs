---
title: "[Mobile] Run the iOS app in the background and wait" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/mobile-run-ios-app-in-background-and-wait.html 
redirect_from:
    - "/display/KD/%5BMobile%5D+Run+iOS+App+in+Background+and+Wait/"
    - "/display/KD/%5BMobile%5D%20Run%20iOS%20App%20in%20Background%20and%20Wait/"
    - "/x/pI0Y/"
    - "/katalon-studio/docs/mobile-run-ios-app-in-background-and-wait/"
description: 
---
Description  
-------------

Run the active application in the background.

> Notes:
> 
> This keyword is used for iOS applications only.

Parameters  
------------

| Param | Param Type | Mandatory | Description |
| --- | --- | --- | --- |
| seconds | int | Required | Amount of time (in seconds) for the application to run in the background. |
| flowControl | FailureHandling | Optional | Specifies the [failure handling](https://docs.katalon.com/katalon-studio/docs/failure-handling.html) schema to determine whether the execution should be allowed to continue or stop. |

Example 
--------

You want to run your iOS application in the background and wait for 10 seconds. 

```groovy
import com.kms.katalon.core.mobile.keyword.MobileBuiltInKeywords as Mobile
import internal.GlobalVariable as GlobalVariable

'Start application on current selected iOS device'
Mobile.startApplication(GlobalVariable.G_iOSApp, false)

'Run the appication in background and wait for 10 seconds'
Mobile.runIOSAppInBackgroundAndWait(10)

'Close application on current selected iOS device'
Mobile.closeApplication()
```