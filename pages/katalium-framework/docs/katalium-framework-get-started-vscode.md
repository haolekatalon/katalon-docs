---
title: "Get Started with Katalium Framework in Visual Studio Code" 
sidebar: katalon_studio_docs_sidebar
permalink: katalium-framework/docs/katalium-framework-get-started-vscode.html 
description:
---

## Prerequisites

* Visual Studio Code.
* Java Development Kit 8.

## Install Katalium Extension for Visual Studio Code

Install Katalium Extension [here](https://marketplace.visualstudio.com/items?itemName=katalon-llc.katalium).

## Activate

In Visual Studio Code, enter Katalon email and password to activate.

![](https://github.com/katalon-studio/docs-images/raw/master/katalium-framework/docs/katalium-framework-get-started-vscode/activate.gif)

## Create project

Click **Create Project** button to create a new project.

_Note: Clean your Workpace folder before creating a new project._

## Start Katalium Server

To start Katalium Server, click **Start Server** button.

_Note: You can view server information in Output tab of Katalium. For example:_

![](https://github.com/katalon-studio/docs-images/raw/master/katalium-framework/docs/katalium-framework-get-started-vscode/before-start-server-vscode.png)

After starting server, open browser in http://localhost:4444/.

![](https://github.com/katalon-studio/docs-images/raw/master/katalium-framework/docs/katalium-framework-get-started-vscode/start-server-vscode.png)

## Run your first test in Visual Studio Code

![](https://github.com/katalon-studio/docs-images/raw/master/katalium-framework/docs/katalium-framework-get-started-vscode/run-test-vscode.png)

## Run your first test in CLI

To run the default test suite configured in `pom.xml` use `mvn clean test`. Test suites can also be specified using command arguments, e.g. `mvn clean test -Dsurefire.suiteXmlFiles=src/test/resources/testng-parallel.xml`.