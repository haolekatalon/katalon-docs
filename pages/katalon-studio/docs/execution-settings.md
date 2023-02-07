---
title: "Project Settings" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/execution-settings.html 
redirect_from:
    - "/display/KD/Execution+Settings/"
    - "/display/KD/Execution%20Settings/"
    - "/x/cgFO/"
    - "/katalon-studio/docs/execution-settings/"
    - "/display/KD/Emails+Settings/"
    - "/display/KD/Emails%20Settings/"
    - "/x/tAFO/"
    - "/katalon-studio/docs/emails-settings/"
    - "/display/KD/Network+Settings/"
    - "/display/KD/Network%20Settings/"
    - "/x/gQ1O/"
    - "/katalon-studio/docs/network-settings/"
    - "/katalon-studio/docs/network-settings.html"
description:
---

## Project information
### Project name, location, and description

Project information displays the name, the location, and the description of the opened project. To view the project information, go to **Project > Settings > Project Information**.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/execution-settings/KS-PRJ-Project-information-2.png" width="70%" alt="Project information">

### Include/Exclude timestamp in .properties files

> Requirements:
>
> * Katalon Studio version 8.2.5 onwards

From Katalon Studio version 8.2.5 onwards, you can include/exclude timestamp in .properties files. To do so:

- Go to **Project > Settings > Project Information**. 
- Check/Uncheck the **Include/Exclude timestamps in .properties files** box. By default, this box is unchecked for new projects.
- Click **Apply**.

  <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/execution-settings/KS-PRJ-Remove-timestamp.png" width="70%" alt="Include/Exclude timestamp settings">

> Known issues:
>
> This enhancement only applies to:
>
> * Native integrations with Katalon Studio, including Katalon TestOps, Azure DevOps, the **qTest Integration**, **Basic Report**, and **Applitools Integration** plugins.
> * Integration plugins, including the **Jira Integration** and **TestRail Integration** plugins.

## Execution Settings

Execution settings help define the desired behaviors of Katalon Studio during test execution. To access default Execution Settings of a project, from the main menu, select **Project > Settings > Execution**

  <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/execution-settings/KS-PRJ-Execution-settings.png" width="70%" alt="Execution settings">

You can also see the following subviews:

* Launch Arguments
* WebUI
* Web Service

### Default Execution Settings

* **Default execution**: The default environment that Katalon Studio uses for executing test scripts.
* **Log executed test steps**: Decide whether the logs include executed test steps or not. [Learn more](https://docs.katalon.com/katalon-studio/docs/working-with-execution-log.html#log-executed-test-steps).
* **Default wait for element timeout (in seconds)**: The default timeout period that Katalon Studio waits for the application under test to be loaded when executing the automation test.
* **Post-Execution Options**: These options decide the actions that Katalon Studio performs after finishing test execution.
  * Open report: Specify whether the report generated after your test suite's execution finishes is to be opened immediately.
  * Terminate drivers: Specify when any driver remains after execution is terminated.

### Allow editing JVM parameters in Execution Settings

**Requirements**:

* Katalon Studio version 7.2.4+
* An active **Katalon Studio Enterprise** license

You can edit VM arguments in Execution Settings by going to **Project > Settings > Execution > Launch Arguments**.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/execution-settings/KS-PRJ-VM-Arguments.png" width="70%" alt="VM arguments settings">

In the **VM Arguments** tab, enter your arguments. VM Arguments entered in **Executions Settings** of a project change the behavior of a Java process of each execution. For example:

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/execution-settings/KS-VM-arguments-input.png" width="70%" alt="Input VM arguments">

To make sure if the configuration works, please add this simple test case:

```java
import com.kms.katalon.core.util.KeywordUtil
KeywordUtil.logInfo(System.getProperty("testme"))
```

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/execution-settings/hello.png" width="100%" alt="Console log">

Currently, Katalon Studio does not support VM arguments' values containing space. Below is a list of the most used JVM Parameters:

Specify minimal and maximal heap sizes

* `-Xms<heap size>[unit]`
* `-Xmx<heap size>[unit]`
* `-XX:MaxMetaspaceSize=<metaspace size>[unit]`

Garbage Collection implementation types

* Serial Garbage Collector: `-XX:+UseSerialGC`
* Parallel Garbage Collector: `-XX:+UseParallelGC`
* CMS Garbage Collector: `-XX:+USeParNewGC`
* G1 Garbage Collector: `-XX:+UseG1GC`

Garbage Collection Logging

* Specify the log file rolling policy: `-XX:+UseGCLogFileRotation`
* Denote the max number of log files that can be written for a single application life cycle: `-XX:NumberOfGCLogFiles=< number of log files >`
* Specify the max size of the file: `-XX:GCLogFileSize=< file size >[ unit ]`
* Denote the file's location: `-Xloggc:/path/to/gc.log`

Handling Out of Memory

* Dump heap into physical file in case of OutOfMemoryError: `-XX:+HeapDumpOnOutOfMemoryError`
* Denote the path where the file is to be written: `-XX:HeapDumpPath=./java_pid<pid>.hprof`
* Issue emergency commands to be executed in case of out of memory error: `-XX:OnOutOfMemoryError="< cmd args >;< cmd args >"`
* Limits the proportion of the VM's time that is spent in GC before an OutOfMemory error is thrown: `-XX:+UseGCOverheadLimit`

### WebUI Settings

You can set default settings for Web UI test execution by going to **Project > Settings > Execution > WebUI**.

  <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/execution-settings/KS-PRJ-WebUI-settings.png" width="70%" alt="WebUI settings">

These settings decide Katalon Studio's behaviors when executing WebUI test in a project.

* **Default Smart Wait**: Tell the web driver to wait for the web page to become static before any operations are performed. [Learn more](https://docs.katalon.com/katalon-studio/docs/webui-smartwait.html).
* **Default wait when IE hangs**: Specify Katalon Studio's default waiting time when IE hangs.
* **Default page load timeout**:
  * Wait until the page is loaded: Katalon Studio waits for the web page to load completely.
  * Wait for (in seconds): The default timeout period (in seconds) that Katalon Studio waits for the web page to load.
* **Delay between actions**: The time for Katalon Studio to wait between test steps when executing test cases.
  * in seconds: This option is selected by default.
  * in milliseconds: This option is supported in Katalon version 7.3+.

See also:

* [Self-healing Tests for Web UI](https://docs.katalon.com/katalon-studio/docs/self-healing.html).

### Web Service Settings

**Requirements**

* Katalon Studio version 7.6 onwards
* An active Katalon Studio Enterprise license

You can set default settings for Web Service test execution by going to **Project > Settings > Execution > Web Service**. The following global configurations are applied to both RESTful and SOAP requests in a project.

  <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/execution-settings/KS-PRJ-Web-service-settings.png" width="70%" alt="Web Service settings">

* **Connection Timeout in milliseconds (0=unlimited)**: The time to establish the connection with the remote server. When it is set to 0 or left empty, Katalon waits for a response forever.
* **Socket Timeout in milliseconds (0=unlimited)**: The time waiting for data – after establishing the connection.
* **Max Response size in bytes**: The maximum number of bytes Katalon Studio renders from a response. When it is set to 0 or left empty, Katalon Studio downloads a response regardless of its size. Please note that downloading a large response may affect the application's performance.

For your convenience, we provide a shortcut to these global settings in a test request's view.

  <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/execution-settings/timeout-maxsize.png">

### Web Service Settings in Script view

**Requirements**

* Katalon Studio version 7.6 onwards
* An active Katalon Studio Enterprise license

You can set request timeout and maximum response size via a script using the built-in functions of Katalon Studio.

**Request Timeout**

* Override timeout settings of a project in a test case

```java
Map<String, Object> generalSettings = RunConfiguration.getExecutionGeneralProperties()
generalSettings.put(RunConfiguration.REQUEST_CONNECTION_TIMEOUT, 3500)
generalSettings.put(RunConfiguration.REQUEST_SOCKET_TIMEOUT, 3500)
```

* Change timeout settings of a specific test request

```java
RequestObject request = findTestObject("Object Repository/Localhost")
request.setConnectionTimeout(3500)
request.setSocketTimeout(3500)

// Or to unset the timeout
request.setConnectionTimeout(RequestObject.TIMEOUT_UNSET)
request.setSocketTimeout(RequestObject.TIMEOUT_UNSET)

// Or to set the timeout to unlimited
request.setConnectionTimeout(RequestObject.TIMEOUT_UNLIMITED)
request.setSocketTimeout(RequestObject.TIMEOUT_UNLIMITED)

// Or if you just want to set to its default value (The default value is set to unlimited)
request.setConnectionTimeout(RequestObject.DEFAULT_TIMEOUT)
request.setSocketTimeout(RequestObject.DEFAULT_TIMEOUT)
```

**Maximum Response Size**

> Katalon Studio also supports setting the maximum response size of execution using `-maxResponseSize` in the command line. [Learn more](https://docs.katalon.com/katalon-studio/docs/console-mode-execution.html#general-options)

* Override response size limit of a project in a test case

```java
Map<String, Object> generalSettings = RunConfiguration.getExecutionGeneralProperties()
generalSettings.put(RunConfiguration.REQUEST_MAX_RESPONSE_SIZE, 400)
```

* Change maximum response size setting of a specific test request

```java
RequestObject request = findTestObject("Object Repository/Basic Auth")
request.setMaxResponseSize(400)

// Or to unset response size limit. And so, the project's max response size setting will be used.
request.setMaxResponseSize(RequestObject.MAX_RESPONSE_SIZE_UNSET)

// Or to set response size limit to unlimited
request.setMaxResponseSize(RequestObject.MAX_RESPONSE_SIZE_UNLIMITED)

// Or if you just want to set to its default value (The default value is set to unlimited)
request.setMaxResponseSize(RequestObject.DEFAULT_MAX_RESPONSE_SIZE)
```

## Emails Settings

To learn about Email Settings, see [Emails Settings](https://docs.katalon.com/katalon-studio/docs/emails-settings.html).

## Network settings

### Certificate settings

Katalon Studio supports the capability to bypass certificate validation so that users with protected network policy can work with Katalon Studio as usual. Go to **Project > Settings > Network**:

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/execution-settings/KS-PRJ-Network-settings.png" width=70% alt="Certificate settings">

You are giving two options, including **None** or **Bypass certificate validation**.

* None
* Bypass certificate validation

The configuration here affects both WebUI and Web Service testings.

### Client certificate settings

> Please be noted that the setting for **Client certificate** is only available for **Katalon Studio Enterprise** users.
>
> This setting is only applied for requests in API/Web Services projects.

Katalon Studio can be configured to use the Client Certificate for all requests. To sign all the requests from Katalon Studio, specify the full path to your KeyStore file and the KeyStore Password. The recommended key store format is **PKCS #12** (.p12).

#### Create a Certificate

To generate public and private key pairs (KeyStore and KeyStore Password) for the above configuration, you can use the *keytool* utility that is included in the JDK installation.

1. Open the command prompt and navigate to the bin folder in the JDK folder.

2. Run this command to create a KeyStore:

   `keytool -genkey -alias katalon -keyalg RSA -keystore katalon.keystore`

3. Enter a password for the new KeyStore and provide the utility with the required information (your name, the name of your organization, etc.).

To export a certificate with your public key, run this command:
`keytool -export -alias katalon -file katalon.cer -keystore katalon.keystore`.
