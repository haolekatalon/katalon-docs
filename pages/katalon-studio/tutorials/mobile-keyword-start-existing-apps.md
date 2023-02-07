---
title: "[Mobile] Start Existing Application"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/mobile-keyword-start-existing-apps.html
description: "New keyword added: Start an existing app"
---
> Starting with **Katalon Studio version 6.3.0**, you can run a test on an installed mobile application.

## Description

This keyword is to start an Appium driver and to activate an installed application by its given application ID.

* Keyword name: **startExistingApplication**

* Keyword syntax: `Mobile.startExistingApplication(appId)`

## Parameters

**AppId**:

* Description: ID of the tested application that’s either the package name of an Android app or the bundle identifier of an iOS app.
* Parameter Type: String
* Mandatory: Required

## Example

`'Start an installed Facebook app on the selected Android device'
Mobile.startExistingApplication("com.facebook.katana")`
