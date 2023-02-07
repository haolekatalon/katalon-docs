---
title: "WebDriver Auto-update" 
sidebar: katalon_studio_docs_sidebar
permalink: katalium-server/docs/katalium-webdriver.html 
description: Information about Katalium WebDriver.
---

When Katalium starts, the server will detect the installed browsers and download the compatible WebDriver versions. Supported browsers are Chrome, Firefox, Internet Explorer, and Edge (pre 18).


## Install WebDriver for Microsoft Edge version 18 and newer

Microsoft WebDriver for Microsoft Edge version 18 is a Windows Feature on Demand.

To install run the following in an elevated command prompt:
```
DISM.exe /Online /Add-Capability /CapabilityName:Microsoft.WebDriver~~~~0.0.1.0
```

Please refer to [here](https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/) for more details.