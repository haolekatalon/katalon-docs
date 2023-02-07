---
title: "GraphQL (PoC)"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/graphql.html
redirect_from:
description: 
---

> **Important**
>
> - This Proof of Concept (PoC) is not ready for production use. We recommend using this PoC for evaluation purposes only.
> - Download Katalon Studio version [8.4.0.beta](https://github.com/katalon-studio/katalon-studio/releases/tag/v8.4.0.beta).

This article provides basic information on GraphQL and how to work with GraphQL in Katalon Studio.

## What is GraphQL?

GraphQL is a query language that allows API users to write queries to get the exact data they need from a single request to a single endpoint. GraphQL provides a detailed and easy-to-understand description of the data in your API, making it easier to evolve APIs over time. GraphQL queries get many resources in a single request and always return predictable results. Therefore, GraphQL significantly improves the efficiency and performance of API calls.

To learn more about GraphQL, you can refer to GraphQL documentation: [Introduction to GraphQL](https://graphql.org/learn/).

## GraphQL testing in Katalon Studio

With this GraphQL PoC in Katalon Studio, you can:

- Create a GraphQL test request with RESTful by GET and POST methods, using queries or mutations.
- Use query variables in a GraphQL request.
- Validate GraphQL request and response against schemas.

### Queries and mutations

The most typical GraphQL operations from the perspective of the client are queries and mutations. In terms of the CRUD model (create, read, update, and delete), a query is identical to read, using the GET method. Mutations handle all of the others, which are create, update, and delete.

Testing mutations are essential as it involves testing data access and additions to databases. Mutations modify data in the database and return us a value. Mutations can edit and manipulate the data from the server side.

There are two ways to execute a GraphQL request with RestFUL in Katalon Studio: GET and POST methods. You can put the GraphQL query into the GET query parameter to create a GraphQL test request without using the GraphQL PoC. GraphQL mutations only support the POST method.

### Validate GraphQL request and response against a schema

Since GraphQL returns a response in JSON format, you can validate a GraphQL response against a JSON schema. This action also helps you troubleshoot the error without the HAR file.

You can also validate a GraphQL request body against a GraphQL schema to make sure the request is valid before sending the request to the server. The validation action happens on the server side. You receive the validation results in the **Response** section if you use keywords in the **Verification** tab or the **Log Viewer** if you use keywords in a test case.

## Sending GraphQL queries using Query Parameters

This section shows you an example of how to send GraphQL queries using **Query Parameters**. To learn more details about **Query Parameters**, you can refer to this document: [Parameterize a Web Service Object](https://docs.katalon.com/katalon-studio/docs/parameterize-a-web-service-object.html).

In this example, we want to get country information from the `https://countries.trevorblades.com` website. Do as follows:

1. Create a **Web Service Request** object and choose the **Request Type** as **RESTful**.
2. In the **Web Service Request** object editor, choose the **GET** request method.
3. In the **URL** field, input this GraphQL URL: `https://countries.trevorblades.com/graphql?query=query Query {  country(code: "VN") {    name    native    capital    emoji    currency    languages {      code      name    }  }}`

    Katalon Studio detects the query parameters after the question mark and lists them in the **Query Parameters** table like below:

    - Name: query
    - Value: `query Query {  country(code: "VN") {    name    native    capital    emoji    currency    languages {      code      name    }  }}`

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/graph-ql/query-parameters.png" alt="query parameters" width="100%">

4. Save your request, then click **Test Request and Verify**. In the **Response** tab, the country information is returned as JSON responses.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/graph-ql/query-response.png" alt="query response" width="70%">

## Sending GraphQL queries and mutations in the HTTP Body

POST requests usually use the application or JSON content type in the HTTP Body.

To send a GraphQL query in the **HTTP Body**, do as follows:

1. Create a **Web Service Request** object and choose the **Request Type** as **RESTful**.
2. In the **Web Service Request** object editor, choose the **POST** request method.
3. In the **URL** field, input the GraphQL endpoint URL.

    For example: `https://katalon-sample-graphql-aut.herokuapp.com/graphql`

4. Switch to the **HTTP Body** tab and choose the **GraphQL** body type.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/graph-ql/graph-ql-query.png" alt="GraphQL query" width="100%">

5. In the **Query** textbox, insert your GraphQL query or mutation.

    GraphQL query example:

    ``` groovy
    query {
    findAllBooks {
        id
        title
   	    isbn
        pageCount
        author {
            id
            firstName
            lastName
        }
      }
    }
    ```

    GraphQL mutation example:

    ``` groovy
    mutation {
        deleteBook(id:3)
    }
    ```

6. Save your request, then click **Test Request and Verify**.
7. View the result in the **Response** tab.

Below are some examples of using GraphQL queries and mutations in the test request object:

* Find all books using a GraphQL query

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/graph-ql/find-all-books-query.png" alt="find all books" width="100%">

* Create a new book using a GraphQL mutation

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/graph-ql/create-new-book-mutation.png" alt="create new book" width="100%">

* Modify the name of a book using a GraphQL mutation

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/graph-ql/modify-mutation.png" alt="modify book name" width="100%">

* Delete a book using a GraphQL mutation

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/graph-ql/mutation-delete.png" alt="delete a book" width="100%">

You can add a GraphQL request into a test case. Katalon Studio generates a script that has send request method with a map of variables. Below is a sample test script generated:

``` groovy
res = WS.sendRequest(findTestObject('Country/CountryQueryVarsInVars', [('id') : 'US']))

println CustomKeywords.'util.JSON.jsonBeautify'( res.getResponseBodyContent());
```

Save and run your test case. You can view the result of sending the request in the **Log Viewer** tab.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/graph-ql/send-request-in-a-test-case.png" alt="send request in a test case" width="100%">

## Use GraphQL variables

To use GraphQL variables, do as follows:

1. Switch to the **HTTP Body** tab and choose **GraphQL** body type.
2. In the **Query** textbox, insert your GraphQL query with defined variables.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/graph-ql/query-variables.png" alt="query variable" width="100%">

3. In the **Query Variables** textbox, insert the values of your GraphQL variables.

    Example 1: In the **Query** textbox, input `$id: ID!`, then define `id` in the **Query Variables** textbox:

    ``` groovy
    {
        "id" : "AU"
    }
    ```

    You can also use Katalon Studio variables as inputs for GraphQL variables using the `${variable}` syntax.

    Example 2: In the **Query Variables** textbox, use Katalon Studio variable: `${id}`.

    ``` groovy
    {
        "id" : "${id}"
    }
    ```

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/graph-ql/query-global-variables.png" alt="global variable in query" width="100%">

    Then, navigate to the **Variables** tab and define the variable name: `id` the default value: `"VN"` in our case.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/graph-ql/Variables-tab.png" alt="variables tab" width="100%">

## Validate GraphQL request and response against schemas

To validate a GraphQL request body and the response returns against schemas, do as follows:

1. Create a GraphQL web service request object.
2. In the web service request object editor, switch to the **Verification** tab.
3. In the **Verification** snippets, use the `WS.validateGraphQLBodyAgainstSchema` with the request body and a schema. See [[WS] Validate GraphQL request body against a GraphQL schema (PoC)](https://docs.katalon.com/katalon-studio/docs/ws-validate-graphql-body-schema.html).

    The response returns as the JSON format, so you can also add the `WS.validateJsonAgainstSchema` to validate the response. See [[WS] Validate the response against a JSON schema (PoC)](https://docs.katalon.com/katalon-studio/docs/ws-validate-json-schema.html#validate-the-response-with-a-json-schema).

    For example:

    ```groovy
    import static org.assertj.core.api.Assertions.*

    import com.kms.katalon.core.model.FailureHandling
    import com.kms.katalon.core.testobject.RequestObject
    import com.kms.katalon.core.testobject.ResponseObject
    import com.kms.katalon.core.webservice.keyword.WSBuiltInKeywords as WS
    import com.kms.katalon.core.webservice.verification.WSResponseManager

    import groovy.json.JsonSlurper
    import internal.GlobalVariable as GlobalVariable

    RequestObject request = WSResponseManager.getInstance().getCurrentRequest()

    ResponseObject response = WSResponseManager.getInstance().getCurrentResponse()

    WS.validateGraphQLBodyAgainstSchema(request, "Schema/Country.qls", FailureHandling.CONTINUE_ON_FAILURE)

    WS.validateJsonAgainstSchema(response, "Schema/JSON/CountrySchema.json", FailureHandling.STOP_ON_FAILURE)
    ```

4. Save and click **Test Request and Verify**. You can view the validation result in the **Response** section.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/graph-ql/verification-tab.png" alt="verification result" width="100%">

You can also validate the GraphQL request/ response against schemas in a test case and view the validation result in the **Log Viewer**. For example:

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/graph-ql/test-case-validate.png" alt="validate against schema in a test case" width="100%">

Sample script:

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

RequestObject req = findTestObject('Country/CountryQuerySchema');
if (WS.validateGraphQLBodyAgainstSchema(req, "Schema/Country.qls")) {
	res = WS.sendRequest(findTestObject('Country/CountryQuerySchema'))
	WS.validateAgainstJsonSchema(res, "Schema/JSON/CountrySchema.json")
}
```
