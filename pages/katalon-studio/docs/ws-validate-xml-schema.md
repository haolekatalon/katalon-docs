---
title: "[WS] Validate an XML string against a schema (PoC)" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/ws-validate-xml-schema.html 
redirect_from:
description: 
---

> **Important**
>
> - This Proof of Concept (PoC) is not ready for production use. We recommend using this PoC for evaluation purposes only.
> - Download Katalon Studio version [8.3.1.alpha](https://github.com/katalon-studio/katalon-studio/releases/tag/v8.3.1.alpha).

## Description

Validate an XML response body, request body, or string against an XML schema. The XML schema input can be an XML string, URL, or file path.

## Parameters

### Validate an XML Object with an XML Schema

<table>
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Parameter Type</th>
            <th>Mandatory</th>
            <th>Description</th>
        </tr>
	</thead>
    <tbody>
        <tr>
            <td>xmlObject</td>
            <td>String</td>
            <td>Required</td>
            <td>Specify the XML object that needs to be validated.</td>
        </tr>
        <tr>
            <td>xmlSchema</td>
            <td>String</td>
            <td>Required</td>
            <td>Specify the XML schema used to validate the XML object.</td>
        </tr>
        <tr>
            <td>flowControl</td>
            <td>FailureHandling</td>
            <td>Optional</td>
            <td>Specify <a href="https://docs.katalon.com/katalon-studio/docs/failure-handling.html">failure handling</a> schema to determine whether the execution should be allowed to continue or stop.</td>
        </tr>
	</tbody>
</table>

### Validate the Response with an XML Schema

<table>
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Parameter Type</th>
            <th>Mandatory</th>
            <th>Description</th>
        </tr>
	</thead>
    <tbody>
        <tr>
            <td>response</td>
            <td>ResponseObject</td>
            <td>Required</td>
            <td>Specify the response object that needs to be validated.</td>
        </tr>
        <tr>
            <td>xmlSchema</td>
            <td>String</td>
            <td>Required</td>
            <td>Specify the XML schema used to validate the response object.</td>
        </tr>
        <tr>
            <td>flowControl</td>
            <td>FailureHandling</td>
            <td>Optional</td>
            <td>Specify <a href="https://docs.katalon.com/katalon-studio/docs/failure-handling.html">failure handling</a> schema to determine whether the execution should be allowed to continue or stop.</td>
        </tr>
	</tbody>
</table>

## Returns

<table>
    <thead>
        <tr>
            <th>Parameter Type</th>
			<th>Description</th>
		</tr>
    </thead>
    <tbody>
		<tr>
			<td>boolean</td>
			<td>
				<ul>
					<li><code>true</code>: the response passes the validation.</li>
					<li><code>false</code>: the response doesn't pass the validation.</p>
					</li>
				</ul>
			</td>
		</tr>
	</tbody>
</table>

> Exception:
>
> If Katalon Studio cannot find the schema file or the response doesn't pass the validation, throw: **StepFailedException**.

### Example

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
