---
title: "Validate JSON/ XML string against a schema for API testing (PoC)"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/schema-validation.html
description: This document shows you how to validate JSON/ XML string against a schema for API testing in Katalon Studio.
---

> **Important**
>
> - This Proof of Concept (PoC) is not ready for production use. We recommend using this PoC for evaluation purposes only.
> - Download Katalon Studio version [8.3.1.alpha](https://github.com/katalon-studio/katalon-studio/releases/tag/v8.3.1.alpha).

Testing API responses against a schema is an efficient and effective way to make sure that APIs are working as expected.

This document shows you how to validate a JSON/ XML response body, request body, or string against a JSON/ XML schema for API testing in Katalon Studio. You can find a sample project for this PoC on our GitHub repository: [Schema Validation Sample Project](https://github.com/katalon-studio-samples/studio-schema-validation-example).

With this PoC, you can:

- Use JSON schema to validate Restful response or request body content.
- Use XML schema to validate Restful and SOAP response or request body content.

## What is a schema?

A schema concisely describes the structure of other instances, which can be used to require that an instance satisfies a certain number of criteria. The document being validated or described is called the instance, and the document containing the description is called the schema. A schema validation asserts constraints on the structure of the instance data. Recently, there has been a lot of interest in using schemas, such as a JSON or XML schema, as a basis for contract testing.

The infographic below demonstrates the role of JSON/XML schema in API testing:

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/schema-validation/Validate-Format.png" alt="inforgraphic" width=60%>

<p align=center><em>Infographic based on the Automation Step By Step course: What is JSON Schema</em></p>

You can learn more from the JSON Schema documentation: [What is a schema?](https://json-schema.org/understanding-json-schema/about.html#about)

## Validate against a JSON/ XML schema in the web service object view

This section walks you through adding schema validation to a web service request and viewing results.

1. Open or create a new **Web Service Request**. To create a new Web Service Request, go to **Test Explorer > Object Repository**. Right-click and choose **New > Web Service Request**.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/schema-validation/new-web-service-request.png" alt="new web service request" width=70%>

2. Switch to the **Validation** tab.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/schema-validation/XMLObjectValidationUI.png" alt="validation" width="100%">

3. To add new validation, click on **Add** and input the below information:

<table>
    <thead>
        <tr>
            <th>Option</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Name</td>
            <td>Name of the validation.</td>
        <tr>
            <td>Type</td>
            <td>
                <ul>
                    <li>JSON Schema</li>
                    <li>XML Schema</li>
                    <li>Auto Detect</li>
                </ul>
            </td>
        <tr>
            <td>Data Type</td>
            <td>
                <ul>
                    <li>Text: Commonly used for simple schemas.</li>
                    <li>File: JSON or XML schema file.</li>
                    <li>Auto detect</li>
                </ul>
            </td>
        <tr>
            <td>Data</td>
            <td>Input a schema, URL to a schema, or file path of a schema. If the <strong>Data Type</strong> is a file, you can click on <strong>Browse</strong> on the <strong>Data</strong> cell to browse to the schema file location.</td>
        </tr>
        <tr>
            <td>Target</td>
            <td>
                <ul>
                    <li>Response Body: check the response body.</li>
                    <li>Request Body: check the request body.</li>
                    <li>Request/Response: check both response and request body.</li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

4. Validate against the schema:

    When you're done adding validation, hit **Save**. Click on the dropdown menu of the **Test Request**, choose **Test Request And Verify**. 
    
    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/schema-validation/test-request-and-verify.png" alt="test request and verify" width=30%>

5. View validation results:
    
    In the **Result** column of the **Validation** tab, the schema validation results appear:

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/schema-validation/XMLObjectValidationUIWithResult.png" alt="result" witdh="100%">

    - **Pass**: the response passes the validation.
    - **Issue(s)**: the response does not pass the validation.

    Click on the result cell to view more details. The **Problem** table appears with a list of issues. For example: `$.date is missing but it is required`, or `$.year: integer found, string expected`.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/schema-validation/XMLObjectValidationUIWithResultTabOut.png" alt="result detail" width="100%">

You've successfully validated a JSON/ XML string against a schema using Katalon Studio.

## Validate against schemas in a test case

In this PoC, there are two new keywords for validating against a JSON/ XML schema:

- [[WS] Validate a JSON string against a schema (PoC)](https://docs.katalon.com/katalon-studio/docs/ws-validate-json-schema.html)
- [[WS] Validate an XML string against a schema (PoC)](https://docs.katalon.com/katalon-studio/docs/ws-validate-xml-schema.html)

You can add these keywords directly in a test case to validate against schemas:

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/schema-validation/XMLManual.png" alt="test case with validation keywords" width="100%">

**View the test in script mode**:

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/schema-validation/XMLScript.png" alt="script mode" width="100%">

``` groovy
res = WS.sendRequest(findTestObject('XML'))

String xml = '''<?xml version="1.0" encoding="utf-8"?>
<List>
    <item>
        <id>3</id>
        <username>James Johnson</username>
        <password>789</password>
        <gender>FEMALE</gender>
        <age>75</age>
        <avatar/>
    </item>
</List>'''

String xmlFile = FileUtils.readFileToString(new File("example/xml/person.xml"));

WS.validateXmlSchema(res, "example/xml/person.xsd");
WS.validateXmlSchema(xml, "example/xml/person.xsd");
WS.validateXmlSchema(xmlFile, "http://localhost:8080/api/users/xsd", FailureHandling.STOP_ON_FAILURE);
```

> Notes:
>
> - You can also add the `sendRequestAndVerify` keyword as a test step. This action also sends the current request and executes verification snippets. Learn more about this keyword at our javadoc [Send Request And Verify](https://docs.katalon.com/javadoc/com/kms/katalon/core/webservice/keyword/builtin/SendRequestAndVerifyKeyword.html) and [Verification Snippets](https://docs.katalon.com/katalon-studio/docs/verification-snippets.html).

When you execute your test, in the **Log Viewer**, you can see the result of those validation steps and a list of issues (if any).

- Validation passed:

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/schema-validation/validate-success.png" alt="validation passed" width="100%">

- Validation failed:

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/schema-validation/validation-failed.png" alt="validation failed" width="100%">

- Validation failed with root causes:

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/schema-validation/validation-failed-root-cause.png" alt="validation failed with root causes" width="100%">
