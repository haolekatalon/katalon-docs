---
title: "[Mobile] Verify element text"
sidebar: katalon_studio_docs_sidebar
permalink: /katalon-studio/docs/mobile-verify-element-text.html 
description: 
---
## Description

Verify the text of an element.

## Parameters  

| Param | Param Type | Mandatory | Description |
| --- | --- | --- | --- |
| to | TestObject  | Required | Represent a mobile element |
| expectedText | String | Required | The text of the element that needs verifying |
| flowControl | FailureHandling | Optional | Specify failure handling schema to determine whether the execution should be allowed to continue or stop. To learn more about failure handling settings, you can refer to this document: [Failure Handling](https://docs.katalon.com/katalon-studio/docs/failure-handling.html#default-failure-handlingbehavior). |

## Returns

 Param | Description |
| --- | --- |
| boolean | **true** if the element has the desired text, otherwise **false**. | 

## Example

Here, we want to verify if the **Views** button has the correct *Views* label.

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

'Start the application on the selected Android device'
Mobile.startApplication(GlobalVariable.G_AndroidApp, false)

'Verify if the 'Views' button has the same label as expected'
Mobile.verifyElementText(findTestObject('Object Repository/Application/android.widget.TextView - Views'), 'Views')

'Close the application on the selected Android device'
Mobile.closeApplication()

```