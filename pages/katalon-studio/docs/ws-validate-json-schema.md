---
title: "[WS] Validate JSON string against a schema (PoC)" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/ws-validate-json-schema.html 
redirect_from:
description: 
---

> **Important**
>
> - This Proof of Concept (PoC) is not ready for production use. We recommend using this PoC for evaluation purposes only.
> - For version [8.3.1.alpha](https://github.com/katalon-studio/katalon-studio/releases/tag/v8.3.1.alpha), this keyword name is `WS.validateJsonSchema`.
> - For version [8.4.0.beta](https://github.com/katalon-studio/katalon-studio/releases/tag/v8.4.0.beta) onwards, this keyword name is `WS.validateJsonAgainstSchema`.

## Description

Validate a JSON response body, request body, or string against a JSON schema. The JSON schema input can be a JSON string, URL, or file path.

## Parameters

### Validate a JSON Object with a JSON Schema

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
            <td>jsonObject</td>
            <td>String</td>
            <td>Required</td>
            <td>Specify the JSON object that needs to be validated</td>
        </tr>
        <tr>
            <td>jsonSchema</td>
            <td>String</td>
            <td>Required</td>
            <td>Specify the JSON schema used to validate the JSON object.</td>
        </tr>
        <tr>
            <td>flowControl</td>
            <td>FailureHandling</td>
            <td>Optional</td>
            <td>Specify <a href="https://docs.katalon.com/katalon-studio/docs/failure-handling.html">failure handling</a> schema to determine whether the execution should be allowed to continue or stop.</td>
        </tr>
	</tbody>
</table>

### Validate the Response with a JSON Schema

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
            <td>Specify the response object that needs to be validated</td>
        </tr>
        <tr>
            <td>jsonSchema</td>
            <td>String</td>
            <td>Required</td>
            <td>Specify the JSON schema used to validate the response object.</td>
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
## Example

### Validate a JSON Object against a schema

``` groovy
import com.kms.katalon.core.webservice.keyword.WSBuiltInKeywords as WS

String jsonPass =
"""
{
  "\$id": "https://example.com/person.schema.json",
  "\$schema": "https://json-schema.org/draft/2020-12/schema",
  "title": "Person",
  "type": "object",
  "properties": {
    "firstName": {
      "type": "string",
      "description": "The person's first name."
    },
    "lastName": {
      "type": "string",
      "description": "The person's last name."
    },
    "age": {
      "description": "Age in years which must be equal to or greater than zero.",
      "type": "integer",
      "minimum": 0
    }
  }
}
"""

String jsonObject = 
"""
{
  "firstName": "White"
  "lastName": "Walter"
  "age": 52
}

"""

boolean successful = WS.validateJsonSchema(jsonObject,jsonPass)
```

### Validate a Response against a schema

``` groovy
import com.kms.katalon.core.testobject.ResponseObject
import com.kms.katalon.core.webservice.keyword.WSBuiltInKeywords as WS
import com.kms.katalon.core.webservice.verification.WSResponseManager

ResponseObject response = WSResponseManager.getInstance().getCurrentResponse()

String jsonPass =
"""
{
  "\$id": "https://example.com/person.schema.json",
  "\$schema": "https://json-schema.org/draft/2020-12/schema",
  "title": "Person",
  "type": "object",
  "properties": {
    "firstName": {
      "type": "string",
      "description": "The person's first name."
    },
    "lastName": {
      "type": "string",
      "description": "The person's last name."
    },
    "age": {
      "description": "Age in years which must be equal to or greater than zero.",
      "type": "integer",
      "minimum": 0
    }
  }
}
"""

boolean successful = WS.validateJsonSchema(response,jsonPass)
```
