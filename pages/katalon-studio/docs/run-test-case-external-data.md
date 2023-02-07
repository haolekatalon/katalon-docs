---
title: "Run Test Case with an external data source"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/run-test-case-external-data.html
description: Guidelines about how to run test case with an external data in Katalon Studio
---
Katalon Studio provides the ability to execute automation test with external data sources.

## Create/Import test data files

To create a new data file, go to **File** > **New** > **Test Data**. Katalon allows you to use external or internal data sources for test execution.
To learn how to create/import a new test data file to Katalon Studio, you can refer to this document: [Manage test data](https://docs.katalon.com/katalon-studio/docs/manage-test-data.html). You can preview the imported test data as follows:

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/run-test-case-external-data/KS-830-Test-data-file.png" width=100% alt="Test data file">


## Create a new Test Suite with Test Case Variables

Open a Test Suite, select **Add** from the command toolbar. All test cases in Katalon Studio will be displayed in the **Test Case Browser** dialog. The selected test case will be added to the test case list like the following example.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/run-test-case-external-data/KS-830-Add-tc.png" width=100% alt="Add test case with variables to the test suite">

## Manage Data Binding

1. In the test suite editor, click **Show Data Binding** to expand the **Data Binding** section with the **Test Data** and **Variable Binding** tables.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/run-test-case-external-data/KS-830-Show-data-binding.png" width=100% alt="Show data binding">

2. In the **Test Data** table, select **Add** > select the data to be used for execution > the selected test data are added to the list accordingly.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/run-test-case-external-data/KS-830-Add-test-data.png" width=100% alt="Add test data">

3. In the **Data Binding** table which displays all variables of the selected test case, select all rows > choose **Set Type** > select **Data Column** as their types.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/run-test-case-external-data/KS-830-Set-data-type.png" width=70% alt="Set data type">

4. Click **Set Test Data** to decide which test data from the list to be used for execution.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/run-test-case-external-data/KS-830-Set-test-data.png" width=70% alt="Set test data">

5. Click each cell in the **Value** column to specify the data field in the selected data file. For example:

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/run-test-case-external-data/KS-830-Set-data-value.png" width=70% alt="Set test data value">

    > Tips:
    >
    > * If the variables and the data field in the selected data files share the same name, you can quickly map all the variables with the data fields in the data file by clicking **Map All**. For example, with this function, the 'Employee', 'Department', and 'Position' variables automatically map with the 'Employee', 'Department', and 'Position' columns of the test data.
    >
    ><img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/run-test-case-external-data/KS-830-Map-all.png" width=70% alt="Map all">

6. After finishing all the steps above, save and run your test suite to see the following result:

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/run-test-case-external-data/8-result.png" width=100% alt="Log viewer">

## See also

* [Combine multiple data sources](https://docs.katalon.com/katalon-studio/docs/combine-multiple-data-sources.html)
