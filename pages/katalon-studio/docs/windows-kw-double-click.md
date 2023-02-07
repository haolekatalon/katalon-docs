---
title: "[Windows] Double-click"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/windows-kw-double-click.html
---
> Starting from **version 7.0.0**, Windows desktop application testing is available on Katalon Studio.

## doubleClick

* **Description**: Perform a double-clicking action on the Web element found by using the locator value of the given Windows object.
* **Keyword name**: doubleClick
* **Keyword syntax**: Windows.doubleClick(windowsObject)
* **Parameter:** windowsObject
  * Description: An object describing the locator and locator strategy to find a Windows element.
  * Parameter Type: WindowsTestObject
  * Mandatory: Required
* **Example**:

``` groovy
"Double-click on the item element to open the editor"
Windows.doubleClick(findWindowsObject("Object Repository/item"))
```
