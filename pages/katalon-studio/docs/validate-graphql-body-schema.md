---
title: "[WS] Validate GraphQL request body against a GraphQL schema (PoC)" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/ws-validate-graphql-body-schema.html 
redirect_from:
description: 
---

> **Important**
>
> - This Proof of Concept (PoC) is not ready for production use. We recommend using this PoC for evaluation purposes only.
> - Download Katalon Studio version [8.4.0 beta](https://github.com/katalon-studio/katalon-studio/releases/tag/v8.4.0.beta).

## Description

Validate a GraphQL request body against a GraphQL schema. The GraphQL schema input can be a GraphQL string, URL, or file path.

## Parameters

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
            <td>request</td>
            <td>RequestObject</td>
            <td>Required</td>
            <td>Specify the request object that needs to be validated.</td>
        </tr>
        <tr>
            <td>graphqlSchema</td>
            <td>String</td>
            <td>Required</td>
            <td>Specify the GraphQL schema used to validate the request.</td>
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
					<li><code>true</code>: the request passes the validation.</li>
					<li><code>false</code>: the request doesn't pass the validation.</p>
					</li>
				</ul>
			</td>
		</tr>
	</tbody>
</table>

> Exception:
>
> If Katalon Studio cannot find the schema file, the request does not have a body content, or the request doesn't pass the validation, throw: **StepFailedException**.

## Example

You want to validate a GraphQL request body against a GraphQL schema before sending the request.

``` groovy

import static com.kms.katalon.core.checkpoint.CheckpointFactory.findCheckpoint
import static com.kms.katalon.core.testcase.TestCaseFactory.findTestCase
import static com.kms.katalon.core.testdata.TestDataFactory.findTestData
import static com.kms.katalon.core.testobject.ObjectRepository.findTestObject
import static com.kms.katalon.core.testobject.ObjectRepository.findWindowsObject
import com.kms.katalon.core.checkpoint.Checkpoint as Checkpoint
import com.kms.katalon.core.cucumber.keyword.CucumberBuiltinKeywords as CucumberKW
import com.kms.katalon.core.mobile.keyword.MobileBuiltInKeywords as Mobile
import com.kms.katalon.core.model.FailureHandling as FailureHandling
import com.kms.katalon.core.testcase.TestCase as TestCase
import com.kms.katalon.core.testdata.TestData as TestData
import com.kms.katalon.core.testng.keyword.TestNGBuiltinKeywords as TestNGKW
import com.kms.katalon.core.testobject.RequestObject
import com.kms.katalon.core.testobject.TestObject as TestObject
import com.kms.katalon.core.webservice.keyword.WSBuiltInKeywords as WS
import com.kms.katalon.core.webui.keyword.WebUiBuiltInKeywords as WebUI
import com.kms.katalon.core.windows.keyword.WindowsBuiltinKeywords as Windows
import internal.GlobalVariable as GlobalVariable
import org.openqa.selenium.Keys as Keys
​
// User wants to validate a GraphQL query in request body before sending the request
RequestObject req = findTestObject('Country/CountryQuerySchema');
String graphQLSchema = 
'''
type Continent {
	code: ID!
	name: String!
	countries: [Country!]!
}
​
type Country {
	code: ID!
	name: String!
	native: String!
	phone: String!
	continent: Continent!
	capital: String
	currency: String
	languages: [Language!]!
	emoji: String!
	emojiU: String!
	states: [State!]!
}
type State {
	code: String
	name: String!
	country: Country!
}
type Language {
	code: ID!
	name: String
	native: String
	rtl: Boolean!
}
input StringQueryOperatorInput {
	eq: String
	ne: String
	in: [String]
	nin: [String]
	regex: String
	glob: String
}
input CountryFilterInput {
	code: StringQueryOperatorInput
	currency: StringQueryOperatorInput
	continent: StringQueryOperatorInput
}
input ContinentFilterInput {
	code: StringQueryOperatorInput
}
input LanguageFilterInput {
	code: StringQueryOperatorInput
}
​
type Query {
	continents(filter: ContinentFilterInput): [Continent!]!
	continent(code: ID!): Continent
	countries(filter: CountryFilterInput): [Country!]!
	country(code: ID!): Country
	languages(filter: LanguageFilterInput): [Language!]!
	language(code: ID!): Language
}
'''
​
if (WS.validateGraphQLBodyAgainstSchema(req, graphQLSchema)) {
	res = WS.sendRequest(req)
}
```
