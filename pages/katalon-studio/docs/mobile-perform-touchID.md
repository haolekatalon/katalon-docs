---
title: "[Mobile] Perform Touch ID" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/mobile-perform-touchID.html 
redirect_from:
description: 
---

> **Requirements**:
>
> * Katalon Studio version 8.3.0 onwards.

## Description

Simulate a Touch ID event on iOS simulators.

> **Notes**:
>
> * To enable this keyword, Touch ID on the simulator must be enrolled.
> * Touch ID and Face ID are available on certain iPhone and iPad models. To learn more about supported iPhone and iPad models, refer to the following Apple documents: [iPhone models](https://support.apple.com/en-us/HT201296) and [iPad models](https://support.apple.com/en-us/HT201471).

## Parameters

| Parameter     | Parameter Type  | Mandatory | Description                                                  |
|---------------|-----------------|-----------|--------------------------------------------------------------|
| `match`       | Boolean         | Yes       | Simulate a successful touch (true) or a failed touch (false). |
| `flowControl` | FailureHandling | No        | Specify failure handling schema to determine whether the execution should be allowed to continue or stop. Refer to: [Failure Handling](https://docs.katalon.com/katalon-studio/docs/failure-handling.html).

## Exceptions

| Throw                 | Precondition                          | Message                                                             |
|-----------------------|---------------------------------------|---------------------------------------------------------------------|
| `StepFailedException` | If Touch ID on the simulator is not enrolled. | To enable this keyword, touch ID on the simulator must be enrolled. |
| `StepFailedException` | If the `performTouchID` keyword is not performed on an iOS simulator. | The `performTouchID` keyword supports iOS simulators only.           |
| `Warning`             | If the `performTouchID` keyword is run on unsupported environments. | The `performTouchID` keyword is not available for physical mobile devices. |                                                        |

## Example

In this example, we want to open the `Authentication.app` application using Touch ID.

```groovy
import static com.kms.katalon.core.checkpoint.CheckpointFactory.findCheckpoint 
import static com.kms.katalon.core.testcase.TestCaseFactory.findTestCase 
import static com.kms.katalon.core.testdata.TestDataFactory.findTestData 
import static com.kms.katalon.core.testobject.ObjectRepository.findTestObject 
import static com.kms.katalon.core.testobject.ObjectRepository.findWindowsObject 
import com.kms.katalon.core.checkpoint.Checkpoint as Checkpoint 
import com.kms.katalon.core.cucumber.keyword.CucumberBuiltinKeywords as CucumberKW 
import com.kms.katalon.core.mobile.keyword.MobileBuiltInKeywords as Mobile 
import com.kms.katalon.core.model.FailureHandling as FailureHandling 
import com.kms.katalon.core.testcase.TestCase as TestCase 
import com.kms.katalon.core.testdata.TestData as TestData 
import com.kms.katalon.core.testng.keyword.TestNGBuiltinKeywords as TestNGKW 
import com.kms.katalon.core.testobject.TestObject as TestObject 
import com.kms.katalon.core.webservice.keyword.WSBuiltInKeywords as WS 
import com.kms.katalon.core.webui.keyword.WebUiBuiltInKeywords as WebUI 
import com.kms.katalon.core.windows.keyword.WindowsBuiltinKeywords as Windows 
import internal.GlobalVariable as GlobalVariable 
import org.openqa.selenium.Keys as Keys

'Start application with Touch ID enrolled on the current selected iOS simulator'
Mobile.startApplication('/Users/katalon/Library/Developer/Xcode/DerivedData/Authenticate_asgsg/Build/Products/Debug-iphonesimulator/Authentication.app', 
    true)

'Perform a successful Touch ID event'
Mobile.performTouchID(true)

'Close application on the current selected iOS simulator'
Mobile.closeApplication()
```