---
title: "[Mobile] Use Fingerprint" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/mobile-use-fingerprint.html 
redirect_from:
description:
---

> **Requirements**:
>
> * Katalon Studio version 8.3.0 onwards.

## Description

Simulate a fingerprint touch event on Android emulators.

> **Notes**:
>
> * To enable this keyword, at least one fingerprint must be enrolled on the emulator via Android Debug Bridge (adb).
> * To learn more about adb, refer to this document on the Android developer site: [Android Debug Bridge](https://developer.android.com/studio/command-line/adb).
> * To learn how to enroll a fingerprint with adb, please refer to the following Android developer guide: [Fingerprint Authentication](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication).

## Parameters

| Parameter       | Parameter Type  | Mandatory | Description                               |
|-----------------|-----------------|-----------|-------------------------------------------|
| `fingerprintId` | Int             | Yes       | An Android fingerprint ID (from 1 to 10). |
| `flowControl`   | FailureHandling | No        | Specify failure handling schema to determine whether the execution should be allowed to continue or stop. Refer to: [Failure Handling](https://docs.katalon.com/katalon-studio/docs/failure-handling.html). |

## Exceptions

| Throw                      | Precondition                          | Message                                                               |
|----------------------------|----------------------------------------|-----------------------------------------------------------------------|
| `IllegalArgumentException` | If the input value for Android fingerprint ID is invalid. | Please enter a valid Android fingerprint ID (from 1 to 10).           |
| `StepFailedException`      | If the `useFingerprint` keyword is not performed on an Android emulator. | The `useFingerprint` keyword supports Android emulators only. |
| `Warning`      | If the `useFingerprint` keyword is run on unsupported environments. | The `useFingerprint` keyword is not available for physical mobile devices.         |

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

'Start application on the current selected Android emulator'
Mobile.startApplication('/Users/katalon/Downloads/Fingerprint.apk', true)

'Simulate fingerprint touch with the desired fingerprint ID'
Mobile.useFingerprint(1)

'Authentication is valid, do some actions'
Mobile.delay(10)

'Close application on the current selected Android emulator'
Mobile.closeApplication()
```