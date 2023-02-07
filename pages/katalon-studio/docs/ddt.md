---
title: "Data-driven Testing with Katalon Studio"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/ddt.html
---

Data-driven testing is a software testing method that stores test data in table or spreadsheet format. Data-driven testing allows testers to input a single test script that can execute tests for all test data from a table and expect the test output in the same table. It is also called table-driven testing or parameterized testing.

Katalon Studio allows you to conduct data-driven testing (DDT) with internal and external data sources at both test case and test suite levels.

> Download the data-driven testing sample project from our Github repository: [Shopping cart sample](https://github.com/katalon-studio-samples/shopping-cart-tests).
## Manage test data

You can configure variable binding to read test data values from internal or external data files such as Excel, CSV, Internal files, and Database. To learn more about managing test data, refer to this document: [Manage test data](https://docs.katalon.com/katalon-studio/docs/manage-test-data.html).

## Set parameter for your test script

You can pass variables to your test scripts by setting parameters in test cases, test objects, or their properties:

* [Test Case Variables](https://docs.katalon.com/katalon-studio/docs/test-case-variables.html)
* [Global Variables](https://docs.katalon.com/katalon-studio/docs/global-variables.html)
* [Parameterize Web Test Objects](https://docs.katalon.com/katalon-studio/docs/parameterize-web-objects.html)
* [Parameterize Mobile Test Object](https://docs.katalon.com/katalon-studio/docs/parameterize-mobile-test-object-properties.html)
* [Parameterize Web Service Object](https://docs.katalon.com/katalon-studio/docs/parameterize-a-web-service-object.html)
* [Parameterize Windows Test Objects](https://docs.katalon.com/katalon-studio/docs/windows-test-objects.html#parameterize-windows-test-objects)

## Supported data-driven testing methods
### In a test case

> Requirements: 
> * You need an active Katalon Studio Enterprise license to execute data-driven testing at the test case level.

Katalon Studio supports data-driven testing at the test case level. To learn more about executing data-driven testing in a test case, you can refer to this document: [Data-driven testing at the test case level](https://docs.katalon.com/katalon-studio/docs/ddt-at-test-case-level.html).

### In a test suite/test suite collection

You can conduct data binding in a test suite with one or multiple external data files:

> Requirements: 
> * You need an active Katalon Studio Enterprise license to perform data-binding with multiple external data sources.

* [Run test case with an external data source](https://docs.katalon.com/katalon-studio/docs/run-test-case-external-data.html)
* [Combine multiple data sources](https://docs.katalon.com/katalon-studio/docs/combine-multiple-data-sources.html) 

Alternatively, you can also conduct data-driven testing with Groovy using the `findTestData` method. To learn about this method, you can refer to our API documentation: [TestData](https://docs.katalon.com/javadoc/com/kms/katalon/core/testdata/TestData.html).

By default, Katalon Studio converts variables to strings to conduct data-binding. However, from Katalon Studio version 6.3.0 onwards, you can enable or disable this function and allow Katalon Studio to read variables as their data types. See: [Enhanced variable binding](https://docs.katalon.com/katalon-studio/docs/bind-as-string.html).

### In a dynamic test suite

Katalon Studio supports data-driven testing in a dynamic test suite. To learn more about executing data-driven testing in a dynamic test suite, you can refer to this document: [Data-driven testing in a dynamic test suite](https://docs.katalon.com/katalon-studio/docs/dynamic-test-suite-ks.html#perform-data-driven-testing-in-a-dynamic-test-suite).



