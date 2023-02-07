---
title: "Test Case Variables"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/test-case-variables.html
description: Guidelines about test case variables and how to call the test case with variables
redirect_from:
    - "/katalon-studio/tutorials/data-driven-testing/"
    - "/katalon-studio/tutorials/data_driven_testing.html"
---
Instead of running test case with hard-coded values, you can run Test Case Variables in Katalon Studio to parameterize your test case or call that test case with different inputs.

Before you start, let’s take a look at the example of test case with hard-coded values:


```
String employee = 'John'
String department = 'Marketing'

println "${employee} - ${department}"
```

## Manage Test Case Variables

In this example, we want to pass variables to the following statement:

```
println "${employee} - ${department}"
```

In the **Variables** tab of the **Test Case Editor**:

1. To add variable using grid view, switch to **Variables** tab of your Test Case.
2. Then click **Add**. A new row is added to the variable list.
3. Input variables.

> Notes: 
> * Remember to save the test case once done.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/test-case-variables/KS-830-tc-variables.png" width=100% alt="test case variables">


The result after running the test case with variables will be the same with hard-coded values:

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/test-case-variables/2-result.png" width=100% alt="test results when running with variables">

## View and declare variables in Script Mode

Switch to **Variable (Script Mode)** tab, Katalon Studio will display a Script Editor with XML format. For example:

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/test-case-variables/KS-830-tc-variables-script.png" width=100% alt="test case variables in script mode">


## Call Test Case with variables

1. Open a Test Case in **Manual** view, then click **Add** and select option **Call Test Case**.

2. The **Test Case Browser** dialog which shows all existing test cases within the project will be displayed. Select the test case to be called and click **OK**.

In the following example, we call the **Test Case with variables** test case.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/test-case-variables/4-test-case-browser.png" width=70% alt="test case variables">


3. A **Call Test Case** step will be added with the selected test case above as its target.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/test-case-variables/KS-830-call-tc-with-variables.png" width=100% alt="call test case with variables">

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/test-case-variables/6-input.png" width=100% alt="call test case with variables">

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/test-case-variables/7-map-input.png" width=100% alt="call test case with variables">


The result after running the test case will be displayed as below:

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/test-case-variables/8-result-after-call-test-case.png" width=100% alt="results of calling test case with variables">

### Call Test Case in Script mode

In **Script** tab, the callTestCase method allows users to make a call to another test case. Refer to the following example:

```
WebUI.callTestCase(findTestCase('Data-driven Testing/Test Case with variables'), [('employee') : 'John', ('department') : 'Marketing', ('position') : 'Manager'], FailureHandling.STOP_ON_FAILURE)
```

