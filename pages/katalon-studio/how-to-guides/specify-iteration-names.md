---
title: "Specify iteration names in data-driven testing reports"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/how-to-guides/specify-iteration-names.html
redirect_from:
description: This document shows you how to differentiate iterations in test reports.
---

This document shows you how to differentiate iterations in test reports.

> Requirements:
>
> - Katalon Studio version 8.3.0 onwards.

> Notes:
>
> - An iteration is a test case executed with a test data row.
> - This feature is available for data-driven tests with test suites. The changes only apply in the test suite HTML reports and the **Test Case Table**.
> - To learn more about data-driven tests, see [Data-driven Testing with Katalon Studio](https://docs.katalon.com/katalon-studio/docs/ddt.html).

When working with data-driven tests, you might want to quickly identify failed data inputs and parts of the Application Under Test (AUT) that might have a problem.

From Katalon Studio version 8.3.0 onwards, you can add a specific variable from the data file at the end of each iteration name. With this input for iteration name or iteration names, you can differentiate between each iteration in your data-driven testing reports at a glance.

## Set iteration names in data binding

To set iteration names using one of the variables in the test data, do as follows:

1. Conduct data-binding from internal data, Excel, CSV, or database data. To learn more about data binding, see [Run Test Case with an external data source](https://docs.katalon.com/katalon-studio/docs/run-test-case-external-data.html).
2. In the **Variable binding** section, click on the **Select** toggle next to **Set Test Name**.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/how-to-guides/specify-iteration-names/set-test-name.png" alt="set test name" width="100%">

3. A list of variables appears. Choose an option to add to your iteration name.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/how-to-guides/specify-iteration-names/select-variable-name.png" alt="select variable name" width="70%">

4. Save and run your test.

## View data-driven testing reports

After you set iteration names in data binding, in the **Test Case Table** and the HTML report, you can see your iteration names are tagged with the chosen variable in the following formula: ` ”Test case name”/”Iteration name” (“Elapsed time“)`.

- In the **Test Case Table**:

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/how-to-guides/specify-iteration-names/test-cases-table.png" alt="test case table" width="100%">
    
    To learn more about **Test Case Table** and reports, see  [Test Suite and Test Suite Collection Reports](https://docs.katalon.com/katalon-studio/docs/test-suite-report.html).

- In the HTML report:

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/how-to-guides/specify-iteration-names/html-report.png" alt="HTML report" width="100%">

    To learn how to export reports to HTML and other formats, see [Export reports to other formats](https://docs.katalon.com/katalon-studio/docs/test-suite-report.html#export-reports-to-other-formats).
