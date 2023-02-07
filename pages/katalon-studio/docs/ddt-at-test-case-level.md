---
title: "Data-driven testing at the test case level"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/ddt-at-test-case-level.html
---

Data-driven testing (DDT) at the test case level allows you to add one or more data files and manage data binding at the test case level. It helps you keep the binding data in the test case independent, regardless of which test suites it is added to. 

This function allows you to:

- Bind each test case to a fixed set of data.
- Run a test case with different test data combinations.
- When executing a test suite containing associated test cases, you can either reuse data binding at the test case level or conduct new data binding in a test suite.

Besides our currently supported data-driven testing methods, this feature also allows you to conduct data-driven testing in a dynamic test suite. To learn more about data-driven testing with dynamic test suites, you can refer to this document: [Data-driven testing in a dynamic test suite](https://docs.katalon.com/katalon-studio/docs/dynamic-test-suite-ks.html#perform-data-driven-testing-in-a-dynamic-test-suite).

> Requirements:
> * Katalon Studio version 8.3.0 onwards.
> * An active Katalon Studio Enterprise license. To learn more about activating your license, you can refer to this document: [Activate Katalon license](https://docs.katalon.com/katalon-studio/docs/activate-license.html#activate-a-license-with-internet-access).

This article demonstrates how to manage data binding at the test case level and execute them in a test suite.

## Conduct data binding at the test case level
### Create a new test data

To create a new data file, go to **File > New > Test Data**. Katalon allows you to use external or internal data sources for test execution. To learn more about creating new data files, you can refer to this document: [Manage Test Data](https://docs.katalon.com/katalon-studio/docs/manage-test-data.html#create-an-excel-test-data).

### Create test case variables

1. Create a new test case. Go to **File > New > Test Case**. Here, we name the test case **DDT at TC level**.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/ddt-test-case-level/830/KS-830-DDT-New-test-case.png" alt="New test case" width=100%>

2. In the new test case, switch to the **Variables** tab. To add test case variables, click **Add**. Input variables in the newly added row.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/ddt-test-case-level/830/KS-830-Variables-tab.png" alt="The variables tab" width=100%>

3. Navigate to the **Data Binding** tab. You can see there are two tables: 

- **Test Data**: Specify here the data files for your test execution.
- **Variable Binding**: This displays all variables input in the **Variables** tab.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/ddt-test-case-level/830/KS-830-Data-binding-tab.png" alt="The data binding tab" width=100%>

    Values input in the **Variables** tab from step 2 will automatically populate in the **Variable Binding** section.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/ddt-test-case-level/830/KS-830-Variables-in-data-binding-tab.png" alt="Input variables appear in the variable binding section" width=100%>

### Conduct data binding

> What is an iteration?
>
> An iteration is a test case executed with a test data row.

To conduct data binding at the test case level, do as follows:

1. In the **Test Data** table:

  - Click **Add** to add one or more data files. A **Test Data Browser** dialog opens.
  
      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/ddt-test-case-level/830/KS-830-DDT-Add-data-files.png" width="70%" alt="Add data files">

  - Select the data files you wish to use for variable binding in the **Test Data Browser** dialog. Click **OK**. The selected test data files appear in the **Test Data** table.

      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/ddt-test-case-level/830/KS-830-DDT-Test-data-browser.png" width="50%" alt="Test Data Browser"><br>
      
      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/ddt-test-case-level/830/KS-830-DDT-Results-after-adding-data.png" width="100%" alt="Results after adding data files">

      > Notes:
      > 
      > * If you are adding a combination of data files, by default, Katalon defines the relationship of multiple data sources at the test case level as One-to-One relationship. You can learn more about the relationship between multiple data files here: [Manage test data relationship](https://docs.katalon.com/katalon-studio/docs/combine-multiple-data-sources.html#manage-test-data-relationship).

  - To specify the data range, double-click on the cell under the **Data Iteration** column of each data file. You can learn more about types of data iterations here: [Modify data range](https://docs.katalon.com/katalon-studio/docs/combine-multiple-data-sources.html#modify-data-range).

2. In the **Variable Binding** table:
   
  - Katalon Studio allows users to **Set Type** for variables all at once if the variables have the same type.  
    In the following example, the **Employee** and **Department** variables have the same type as **Data Column**. Highlight both rows, click **Set Type > Data Column**.  

      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/ddt-test-case-level/830/KS-830-DDT-Set-data-type.png.png" width="70%" alt="Set Data Type">

  - In the **Test Data** column, click on each row to choose the test data files for execution.
       
      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/ddt-test-case-level/830/KS-830-DDT-Choose-test-data-for-data-type.png" width="70%" alt="Choose Test data for Data Type">

  - If the variables and the data field in the selected data files share the same name, you can quickly map all the variables with the data fields in the data file by clicking **Map All**. For example, with this function, the 'Employee' and the 'Department' variables automatically map with the 'Employee' and 'Department' columns of the test data.

      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/ddt-test-case-level/830/KS-830-DDT-Choose-value-for-data-type.png" width="70%" alt="Choose Value for Data Type">

  - Alternatively, you can also click on each row to specify the data field in the selected data file in the **Value** column.

      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/ddt-test-case-level/830/KS-830-Choose-value-different-data.png" width="70%" alt="Choose Value for Data Type">

3. Save the test case and run it. To view your test results, go to the **Log Viewer** tab.

      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/ddt-test-case-level/830/KS-830-DDT-Test-case-results.png" width="70%" alt="Results in Log Viewer">

## Execute test suites containing associated test cases

> What is a suite test case?
>
> A suite test case is a test case in a test suite.

> Notes:
> * To execute test suites in the CLI, Docker, or CI/CD tools, you need an active Katalon Runtime Engine license.
> * For real-time monitoring and better reporting capabilities, consider integrating your project with Katalon TestOps. Learn more about Katalon TestOps integration here: [Upload Test Results to Katalon TestOps from Katalon Studio](https://docs.katalon.com/katalon-studio/docs/katalon-analytics-beta-integration.html).

1. Add the associated test case to a test suite.
2. To conduct data binding, in the test suite editor, click **Show Data Binding**. 
      
    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/ddt-test-case-level/830/KS-830-DDT-Show-data-binding.png" width="100%" alt="Data binding section in the test suite">
      
3. Select the data binding level. You can bind data at the test case (TC) or suite test case (STC) level. The **Use Variables and Binding at Suite Test Case** option is selected by default.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/ddt-test-case-level/830/KS-830-DDT-Data-binding-options.png" width="100%" alt="Data Binding Options">


    <table>
    <thead>
      <tr>
      <th>Options</th>
      <th>Description</th>
      </tr>
    </thead>
    <tbody>
      <tr>
      <td>Use Variables and Binding at Test Case</td>
      <td>With this option:<br>- Katalon executes the associated test case with the data binding at the test case level.<br>- To edit the data binding at the test case level, click the <strong>Test Case</strong> hyperlink. By doing so, the users are navigated to the <strong>Variables & Data Binding</strong> tab of the associated test case.<br><p style="text-align: center;"><a class="pop"><img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/ddt-test-case-level/830/KS-830-DDT-Click-TC-hyperlink.gif" width="70%" alt="Choose the Use Variables and Binding at Test Case option"></a><br><em>Click the gif to enlarge it.</em></p><br>- While selecting the <strong>Use Variables and Binding at Test Case</strong> option, you can not conduct data binding at the suite test case level.<br><p style="text-align: center;"><img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/ddt-test-case-level/830/KS-830-DDT-Warning-at-TC-level.png" width="70%" alt="Choose the Use Variables and Binding at Test Case option"></p></td>
      </tr>
      <tr>
      <td>Use Variables and Binding at Suite Test Case</td>
      <td>With this option:<br>- Katalon executes the associated test case with the data binding at the suite test case level.<br>- You can edit the <strong>Test Data</strong> and <strong>Variable Binding</strong> tables at the STC level. To learn more about binding data at the STC level, you can refer to this document: <a href="https://docs.katalon.com/katalon-studio/docs/run-test-case-external-data.html#manage-data-binding" target="_blank" rel="noopener noreferrer">Manage Data Binding</a>.<br><p style="text-align: center;"><a class="pop"><img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/ddt-test-case-level/830/KS-830-DDT-Binding-suite-test-case.png" width="70%" alt="Choose the Use Variables and Binding at Suite Test Case option"></a><br><em>Click the image to enlarge it.</em></p></td>
      </tr>
    </tbody>
    </table>
        
    > Notes:
    > * In case your test suite has existing data configurations, switching to the **Use Variables and Binding at Test Case** option does not remove the preconfigured data in the suite test case.

4. Once finished, hit **Run** to execute your test suite.  
## Test Reports

After the test suite execution, to view your test reports, go to the **Reports** folder in the **Test Explorer** panel. 

  <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/ddt-test-case-level/830/KS-830-DDT-Reports.png" width="100%" alt="Reports">

> Notes:
> * When running a test suite that uses variables and bindings at the test case level, the total number of executed test cases in test reports is the number of executed iterations. In the above example, we run a test case with 3 different sets of data, we can see the results of three executed test cases in the test reports.


Alternatively, you can also view your reports and details in `<your-project-folder>/Reports`. Katalon Studio supports exporting test reports into different formats, such as HTML, CSV, PDF, and JUnit. You can learn more about exporting reports here: [Generate reports](https://docs.katalon.com/katalon-studio/docs/test-suite-report.html#automatically-generate-reports).

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/ddt-test-case-level/830/KS-830-HTML-report.png" width="100%" alt="Reports">
 





