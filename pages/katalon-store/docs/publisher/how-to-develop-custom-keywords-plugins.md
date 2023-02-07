---
title: "How to develop Custom Keywords Plugins"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-store/docs/publisher/how-to-develop-custom-keywords-plugins.html
redirect_from:
    - "/katalon-store/docs/publisher/how-to-develop-custom-keywords-plugins/"

description: How to develop Custom Keywords Plugins
---
Previously, we have announced a tutorial to [build standard plugins](https://docs.katalon.com/katalon-store/docs/publisher/create-plugin.html) for Katalon Studio.

In this tutorial, we’ll introduce a more lightweight process for sharing custom keywords as plugins.

* Custom Keyword plugin is available since Katalon Studio 6.0.6.

## Develop a Custom Keywords plugin

* Sample: https://github.com/katalon-studio/katalon-studio-excel-custom-keywords-plugin.
* A Custom Keywords plugin is essentially a normal Katalon Studio project with some Custom Keywords implementation. So the steps are quite simple:
  * Create a new Katalon Studio project.
  * Implement your Custom Keywords.
  * Test Cases can be added to help verify these Custom Keywords and to serve as samples for plugin users.

## Package the Custom Keywords plugin

* In the  `Keywords`  folder, add a  `katalon-plugin.json`  file with the following format:

```
{
  "keywords": [keywordClass1, keywordClass2]
}
```

Example:

[github.com](https://github.com/katalon-studio/katalon-studio-excel-custom-keywords-plugin/blob/master/Keywords/katalon-plugin.json)

#### [katalon-studio/katalon-studio-excel-custom-keywords-plugin/blob/master/Keywords/katalon-plugin.json](https://github.com/katalon-studio/katalon-studio-excel-custom-keywords-plugin/blob/master/Keywords/katalon-plugin.json)

```
{
	"keywords": ["com.katalon.plugin.keyword.excel.ExcelReadKeywords", "com.katalon.plugin.keyword.excel.ExcelWriteKeywords"]
}
```

* In the project’s root folder add a  `build.gradle`  file

[github.com](https://github.com/katalon-studio/katalon-studio-excel-custom-keywords-plugin/blob/master/build.gradle)

#### [katalon-studio/katalon-studio-excel-custom-keywords-plugin/blob/master/build.gradle](https://github.com/katalon-studio/katalon-studio-excel-custom-keywords-plugin/blob/master/build.gradle)

```
plugins {
  id 'java'
  id 'groovy'
  id 'com.github.johnrengelman.shadow' version '4.0.4'
  id "com.katalon.gradle-plugin" version "0.0.6"
}

repositories {
  jcenter()
  mavenCentral()
}

sourceSets {
  main {
    groovy {
      srcDirs = ['Keywords', 'Include/scripts/groovy']
      srcDir 'Libs'
    }
  }
}
```

This file has been truncated. [show original](https://github.com/katalon-studio/katalon-studio-excel-custom-keywords-plugin/blob/master/build.gradle)

Install [Gradle](https://gradle.org/) and run the following command, then checking the  `build/libs`  for the plugin’s JAR package.

```
gradle katalonPluginPackage
```

> Note: If you run the above command inside an existing project, please open that project with Katalon Studio first.

## Test the Custom Keywords plugin

* In a new Katalon Studio project, create  `Plugins`  folder and put the plugin’s JAR package here. Reopen this project to use imported Custom Keywords.
* You can find a sample project which uses the above Excel Custom Keywords plugin here https://github.com/katalon-studio-samples/sample-custom-keywords-plugin-usage.

## Publish the plugin

Once you’re done developing your plugins, please [submit them to Katalon Store](https://docs.katalon.com/katalon-store/docs/publisher/submit-plugin.html). We’ll review your contents against [our policies](https://www.katalon.com/terms/#katalon-plugin-license-agreement) before approving to list them on the Store.

## Sample plugins

* https://github.com/katalon-studio/katalon-studio-excel-custom-keywords-plugin
* https://github.com/katalon-studio/katalon-studio-ashot-custom-keywords-plugin
* https://github.com/katalon-studio/katalon-studio-zip-custom-keywords-plugin

