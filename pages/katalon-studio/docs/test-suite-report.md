---
title: "Test Suite and Test Suite Collection Reports"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/test-suite-report.html
redirect_from:
    - "/display/KD/Test+Suite+Report/"
    - "/display/KD/Test%20Suite%20Report/"
    - "/x/v4IY/"
    - "/katalon-studio/docs/test-suite-report/"
    - "/display/KD/Test+Report/"
    - "/katalon-studio/tutorials/viewing_test_suite_reports.html"
    - "/katalon-studio/docs/basic-report.html"
    - "/display/KD/Test+Suite+Collection+Report/"
    - "/display/KD/Test%20Suite%20Collection%20Report/"
    - "/x/7gAM/"
    - "/katalon-studio/docs/test-suite-collection-report/"
    - "/katalon-studio/docs/test-suite-collection-report.html"
    - "/katalon-studio/docs/get-generated-reports-location-at-runtime.html"
    - "/display/KD/Get+generated+Reports+location+at+runtime/"
    - "/display/KD/Get%20generated%20Reports%20location%20at%20runtime/"
    - "/x/ewXR/"
    - "/katalon-studio/docs/get-generated-reports-location-at-runtime/"
    - "/display/KD/Video+Capturing/"
    - "/display/KD/Video%20Capturing/"
    - "/x/qRJO/"
    - "/katalon-studio/docs/video-capturing/"
    - "/katalon-studio/docs/video-capturing.html"
description:
---

## Test suite report

You can view reports directly inside each test suite page.

After executing a test suite, to see the test suite report, go to the **Result** tab.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/test-suite-report/KS-835-REPORTS-Test-suite-results-tab.png" width="100%" alt="Results tab"> 

<table><thead><tr><th>Component</th><th>Description</th></tr></thead><tbody><tr><td>Test cases table</td><td>List of executed test cases.</td></tr><tr><td>Summary tab</td><td>Information of the executed environment and summary of the execution result.</td></tr><tr><td>Execution Settings tab</td><td><p>Settings of execution browsers/devices. For example:</p><p style="text-align: center;"><a class="pop"><img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/test-suite-report/KS-835-REPORTS-Execution-settings.png"></a><br><em>Click the image to enlarge it.</em></p></td></tr><tr><td>Execution Environment tab</td><td><p>Other information about the executed system. For example:</p><p style="text-align: center;"><a class="pop"><img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/test-suite-report/KS-835-REPORTS-Execution-environment.png"></a><br><em>Click the image to enlarge it.</em></p></td></tr></tbody></table>

### Test cases table

The summary information of all executed iterations done in the test suite is displayed here. Each time when a test case is executed with a test data row is considered an iteration.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/test-suite-report/KS-835-REPORT-test-case-table.png" width="100%" alt="Test cases list"> 

You can filter reports based on their execution status:

| Filter | Description |
| --- | --- |
| Passed | Show only iterations which are passed. |
| Failed | Show only iterations which are failed. |
| Error | Show only iterations having errors. |
| Incomplete | Show only incomplete iterations. |
| Skipped | Show only skipped iterations. |

If qTest and JIRA are configured in project settings, you can submit data to those systems. To learn more about qTest and Jira integration, you can refer to the following documents:
- [qTest Integration](https://docs.katalon.com/katalon-studio/docs/qtest-integration.html)
- [JIRA Integration](https://docs.katalon.com/katalon-studio/docs/jira-integration.html)

### Test suite summary

This section gives the summary information of the test suite:

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/test-suite-report/KS-835-REPORTS-Summary.png" width="100%" alt="Test suite summary"> 


| Field | Description |
| --- | --- |
| **Test Suite ID** | The ID of the executed test suite in Katalon Studio. |
| **Hostname** | The hostname of the environment where the test suite was executed. |
| **Local OS** | The OS used to open Katalon Studio. |
| **Platform** | The OS, browser, and browser version used to execute the test. |
| **Start / End / Elapse** | Execution start/end date time and duration. |
| **Total TC** | Total number of test cases and their execution status. |

### Test case log details

To view details of the executed logs, in the **Test Case Table**, select an iteration and click **Show Test Case Details**.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/test-suite-report/KS-835-REPORT-Show-test-case-details.png" width="80%" alt="Show Test Cases Details"> 

1. **Test Log** tab

    Details regarding all the executed steps and their status are displayed in this tab. 

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/test-suite-report/KS-835-REPORT-test-log.png" width="80%" alt="Test log tab"> 

    <table><thead><tr><th>Component</th><th>Description</th></tr></thead><tbody><tr><td>Test Log <strong>Information</strong> tab</td><td>Information of the test step selected in the <strong>Test Case's Log</strong> section:<ul><li>The <strong>Name</strong> of the test step (the name of the keyword used in the test step)</li><li>Execution <strong>Start/End</strong> date time and duration</li><li>The <strong>Description</strong> of the test step</li><li>Any system <strong>Message</strong> raised when the test step was executed</li></ul></td></tr><tr><td>Test Log <strong>Image</strong> tab</td><td><p>The screenshot taken from the application under test, it is captured in either of the following situations:</p><ul><li>An error occurs during test execution</li><li>The <code>take screenshot</code> keyword is used. To learn more about the <code>take screenshot</code> keyword, you can refer to the following document: <a href="https://docs.katalon.com/katalon-studio/docs/webui-take-screenshot.html" target="_blank" rel="noopener noreferrer">[WebUI] Take Screenshot</a></li></ul></td></tr></tbody></table>

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/test-suite-report/KS-835-REPORT-image-tab.png" alt="test log image tab" width="80%">

   You can determine which type of information to be displayed by using the provided filters:

    | Filter | Description |
    | --- | --- |
    | Info | Show the messages logged for information/reference. |
    | Passed | Show the steps which are successfully executed. |
    | Failed | Show the steps which are failed to execute. |
    | Error | Show the steps having errors. |
    | Incomplete | Show incomplete steps due to other factors such as wrong syntax, power shortage, disconnected network, etc... |
    | Warning | Show the steps which have warning status. |
    | Not Run | Show the skipped steps. |

    If you have configured Jira integration, you can submit a ticket to this system. For further details, you can refer to this document: [Submit an issue to Jira](https://docs.katalon.com/katalon-studio/docs/jira-integration.html#submit-an-issue-to-jira).

    Screenshots are taken for the failed steps, and you can hover the mouse cursor over the attachment icon to review.

2. **Information** tab

    You can find the summary information of the test case in this tab.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/test-suite-report/KS-835-REPORT-information-tab.png" width="80%" alt="Information tab"> 

    | Field | Description |
    | --- | --- |
    | **Test Case ID** | The ID of the executed test case in Katalon Studio. |
    | **Start / End / Elapse** | Execution start/end date time and duration. |
    | **Description** | The description of the test case. |
    | **Message** | Any system message raised when this iteration was executed. |

3. **Integration** tab

    The information regarding qTest or JIRA integration of this iteration is displayed in this tab.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/test-suite-report/integration-tab.png" width="40%" alt="Integration tab"> 

## Test suite collection report

You can view reports directly inside each test suite collection page. Test suite collection reports are only available for Katalon Studio Enterprise users.

After executing a test suite collection, to see the test suite collection report, go to the **Result** tab.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/test-suite-report/KS-REPORTS-Results-of-the-TSC.png" width="100%" alt="Test suite collection report">


| Field | Description |
| --- | --- |
| **ID** | The ID of the executed test suite in Katalon Studio. |
| **Environment** | The environment in which the test suite is executed. |
| **Status** | Information about whether the execution is completed or not. |
| **Failed Tests / Total** | Total test cases in the test suite and the number of failed test cases, if any. |
| **Test Suite Details** | Shows test suite reports, see above: [Test suite reports](https://docs.katalon.com/katalon-studio/docs/test-suite-report.html#test-suite-report). |

## Report history

> Report History is only available for Katalon Studio Enterprise users.

Once a test suite/test suite collection finishes its execution, a report is automatically generated and stored in the **Reports** folder.

For example:

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/test-suite-report/KS-825-REPORT-history.png" width="50%" alt="Test suite history reports">

The report is named with the following naming convention: _YYYYMMDD_HHmmss_, corresponding to the date and time of the start of the execution.

## Export reports to other formats

For the purpose of sharing, you can export reports of test suites into other formats such as **HTML**, **CSV**, **PDF**, and **JUnit**.

> Notes:
>
> * Starting in version 7.0.0, Katalon Studio automatically generates JUnit reports for both test suite and test suite collection.

### Automatically generate reports

In **Project > Settings > Plugins > Report**, select your preferred format for the reports generated after each test suite execution.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/test-suite-report/KS-REPORTS-Reports-settings.png" width="70%" alt="Reports settings">

Execute a test suite and observe the *Log Viewer* after the test execution completes. The generated reports are the same as the settings you have configured above.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/Basic%20Report/log-viewer.png" width="391" alt="Report generator in the log viewer">

You can view the generated reports in `<project_folder>\\Reports\\<execution_folder>` after the test execution finishes.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/Basic%20Report/report-folder.png" width="" alt="report folder">

### Manually export reports

For test suite collection, you can export to **HTML** format only. To manually export reports, do as follows:

1. Open the **Result** view of a test suite or a test suite collection.
2. On the top right corner, select **Export report**. Then, choose a format to export.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/test-suite-report/KS-REPORTS-Export-reports-manually.png" width="100%" alt="Manually export reports">

## Get generated reports location at runtime

To retrieve current generated reports location, you can use the sample code below:

```groovy
import com.kms.katalon.core.configuration.RunConfiguration
RunConfiguration.getReportFolder()
```

You can also retrieve other information through the RunConfiguration package, see: [RunConfiguration](https://api-docs.katalon.com/com/kms/katalon/core/configuration/RunConfiguration.html).

## Video capturing

> Notes:
>
> * K-Lite Codec is recommended to play the Katalon Studio test execution videos. You can download K-Lite Codec on the Codec Guide website: [K-Lite Codec](https://www.codecguide.com/download_kl.htm).
> * Support execution at the test suite level.
> * Support all browsers except for Remote, Headless, Kobiton, and Custom. For remote or headless browsers, it's recommended to use [Katalium Server](https://docs.katalon.com/katalium-server/docs/katalium-server-katalon-studio-remote-machine.html) to view captured sessions.
> * Recording parallel execution is NOT supported yet.

Debugging can be time-consuming and challenging for many automation testers. Katalon Studio helps solve this problem by supporting you with the ability to capture test execution via video format. You can enable the video capturing feature in **Project Settings**.

Follow the steps below to see how to work with Katalon Studio video capturing feature:

1. After creating a test suite in Katalon Studio, select **Project > Settings > Execution**. Check the **Enable Video Recorder during execution** option.

    By default, Katalon Studio only captures **Failed** test cases. However, you can select options to capture only the **Passed**/**Failed** test cases or both.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/test-suite-report/KS-REPORTS-Enable-video-recording.png" width="100%" alt="Enable video capturing">

    Video settings can be specified based on the preferences of users. Katalon Studio recommends AVI (`.avi`) format and low quality to save disk space. The higher the video quality is, the bigger the file size is.

    * **Video format**: AVI (`.avi`) or MOV (`.mov`)
    * **Video quality**: Low; Medium or High

2. After executing a test suite, navigate to the **Result** tab. You can view the list of test cases in the test cases table with its video attached accordingly.
    
    To play the video, click on the play icon in the **Video** column. Test steps descriptions are embedded as a subtitle.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/test-suite-report/KS-835-REPORTS-Enable-video-recording.png" width="100%" alt="View video capturing">

By watching how the automated test was executed, the testing team can identify exactly where the test failed. Thus, time and resources are managed more efficiently and effectively.
