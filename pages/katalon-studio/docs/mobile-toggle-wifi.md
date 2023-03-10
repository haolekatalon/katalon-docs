---
title: "[Mobile] Toggle Wifi" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/mobile-toggle-wifi.html 
redirect_from:
description: 
---

> **Requirements**:
>
> * Katalon Studio version 8.3.0 onwards.

## Description

Simulate toggling Wifi on/off on mobile devices.

> **Notes**:
>
> * This keyword supports real iOS devices and Android emulators.
> * On iOS devices, **Access Within Apps** must be enabled. To enable the feature, refer to the following Apple document: [Edit Control Center on your iPhone, iPad, and iPod touch](https://support.apple.com/en-us/HT211812).

## Parameters

| Parameter   | Parameter Type | Mandatory | Description |
| ----------- | -----------    | -----------  | ----------- |
| `mode`        | String      | Yes         | ["no", "off", "false"] to turn off Wifi; ["yes", "on", "true"] to turn on Wifi. |
| `flowControl`   | FailureHandling | No | Specify failure handling schema to determine whether the execution should be allowed to continue or stop. Refer to: [Failure Handling](https://docs.katalon.com/katalon-studio/docs/failure-handling.html). |

## Example

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

'Start application on the current selected Android device'
Mobile.startApplication('/Users/katalon/Downloads/Authentication.apk', true)

'Turn on Wifi on the device'
Mobile.toggleWifi('true')

'Close application on the current selected Android device'
Mobile.closeApplication()
```
