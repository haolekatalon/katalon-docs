---
title: "Using Web Services in a Test Case" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/using-web-services-in-a-test-case.html 
redirect_from:
    - "/display/KD/Using+Web+Services+in+a+Test+Case/"
    - "/display/KD/Using%20Web%20Services%20in%20a%20Test%20Case/"
    - "/x/ARRO/"
    - "/katalon-studio/docs/using-web-services-in-a-test-case/"
description: 
---
Katalon Studio supports various ways to use a Web Service object in a test case. You can call the web service methods from Manual View (keywords test), Script View (test scripts), and verify the responses.  

### In Test Request Object View

You can **add** Web Services request to test case directly from the _object details view_. Simply click on the _plus_ icon to add to _New_ or any _Existing_ test case.

![](https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/using-web-services-in-a-test-case-58/Screen-Shot-2018-09-20-at-5.06.42-PM.png)

### In Test Case editor's Manual View

Follow the steps below to use web service object in **Manual** view:

1.  Open a test case in **Manual** view, then select the option to add a **Web Service Keyword** from command toolbar.  
    ![](https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/using-web-services-in-a-test-case-58/image2017-6-30-203A493A48.png)  
      
    
2.  A Web Service step is added to the test case.   
    To send a request to Web Service, you need to use **[Send Request](/display/KD/%5BWS%5D+Send+Request)** keyword. Select the **[Send Request](/display/KD/%5BWS%5D+Send+Request)** keyword now.  
    ![](https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/using-web-services-in-a-test-case-58/image2018-8-23-163A583A44.png)  
      
    
3.  Double click on object cell to specify the web service object to **[Send Request](/display/KD/%5BWS%5D+Send+Request)**.
    
    > Variables for Web Service Test Object
    > 
    > When you modify the variables of a Web Service Test Object in a test case, the values will ONLY apply to that particular test case. If you reuse that Test Object in another test case, Katalon Studio will get the original values that were defined in the Test Object editor.
    
      
    ![](https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/using-web-services-in-a-test-case-58/image2018-8-23-163A353A40.png)  
      
    
4.  The output of **[Send Request](/display/KD/%5BWS%5D+Send+Request)** keyword could be validated if needed using different **[Verify...](/display/KD/Web+Service)** keywords depending on your situation.  
      
    
### In Test Case editor's Script View

You can use the **[Send Request](/display/KD/%5BWS%5D+Send+Request)** keyword for Web Service object and the **[Verify...](https://docs.katalon.com/katalon-studio/docs/ws-verify-element-property-value.html)** keywords to verify the web service response. You may want to refer to [Handle Response messages](https://docs.katalon.com/katalon-studio/docs/handle-response-messages.html) for more details regarding **Element Locator**:

```groovy
//Send a SOAP request and returns its response
def response = WS.sendRequest(findTestObject([]))
//Verify if a value at a specific location in response is as expected
WS.verifyElementPropertyValue(response, <Element Locator>, <expected value>)
```

For example:

![](https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/using-web-services-in-a-test-case-58/image2017-2-28-153A203A11.png)

If you have used [variables and parameters in test requests](https://docs.katalon.com/katalon-studio/docs/parameterize-a-web-service-object.html#variables-and-parameterizing-request-objects), you can pass values to the variables as follows: 

```groovy
//Send a test request and pass values to variables used in that request
def response = WS.sendRequest(findTestObject([the ID of Web Service object], ["variable1": value1, "variable2": value2, ... , "variableN": valueN]))
```

For example:

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/using-web-services-in-a-test-case/parameterize-ws.png">

The following API docs may prove useful when working with web service objects:

| Class | Description |
| --- | --- |
| **[Request Object](http://api-docs.katalon.com/studio/v4.6.0.2/api/com/kms/katalon/core/testobject/RequestObject.html)** | Describe all available methods for Request Object |
| **[Response Object](http://api-docs.katalon.com/studio/v4.6.0.2/api/com/kms/katalon/core/testobject/ResponseObject.html)** | Describe all available methods for Response Object |