---
title: "Sample Custom Keywords" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/sample-custom-keywords.html 
redirect_from:
    - "/display/KD/Sample+Custom+Keywords/"
    - "/display/KD/Sample%20Custom%20Keywords/"
    - "/x/3QHR/"
    - "/katalon-studio/docs/sample-custom-keywords/"
description: 
---
Since Katalon Studio 5.4

When creating a **New Custom Keyword**, you have the options to generate sample custom keywords used for either Web, Mobile or API testing. They provide a great example to learn how to create custom keywords with proper coding convention in Katalon Studio from scratch.

The options are displayed directly when you create a new custom keyword.

![](https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/sample-custom-keywords/Screen-Shot-2018-03-26-at-13.35.02.png)

| Option | Description |
| --- | --- |
| Generate sample keywords for Web | Generate some sample functions used for Web Testing |
| Generate sample keywords for Mobile | Generate some sample functions used for Mobile Testing |
| Generate sample keywords for API | Generate some sample functions used for API Testing |

  
You can select **one** or **all** of these options to have all sample custom keywords generated in one file. For example, select all options, the generated custom keyword will look like as below:

```groovy
class sampleKeywords {
	/**
	 * Refresh browser
	 */
	@Keyword
	def refreshBrowser() {
		KeywordUtil.logInfo("Refreshing")
		WebDriver webDriver = DriverFactory.getWebDriver()
		webDriver.navigate().refresh()
		KeywordUtil.markPassed("Refresh successfully")
	}

	/**
	 * Click element
	 * @param to Katalon test object
	 */
	@Keyword
	def clickElement(TestObject to) {
		try {
			WebElement element = WebUiBuiltInKeywords.findWebElement(to);
			KeywordUtil.logInfo("Clicking element")
			element.click()
			KeywordUtil.markPassed("Element has been clicked")
		} catch (WebElementNotFoundException e) {
			KeywordUtil.markFailed("Element not found")
		} catch (Exception e) {
			KeywordUtil.markFailed("Fail to click on element")
		}
	}

	/**
	 * Get all rows of HTML table
	 * @param table Katalon test object represent for HTML table
	 * @param outerTagName outer tag name of TR tag, usually is TBODY
	 * @return All rows inside HTML table
	 */
	@Keyword
	def List<WebElement> getHtmlTableRows(TestObject table, String outerTagName) {
		WebElement mailList = WebUiBuiltInKeywords.findWebElement(table)
		List<WebElement> selectedRows = mailList.findElements(By.xpath("./" + outerTagName + "/tr"))
		return selectedRows
	}

	/**
	 * Check if element present in timeout
	 * @param to Katalon test object
	 * @param timeout time to wait for element to show up
	 * @return true if element present, otherwise false
	 */
	@Keyword
	def isElementPresent_Mobile(TestObject to, int timeout){
		try {
			KeywordUtil.logInfo("Finding element with id:" + to.getObjectId())

			WebElement element = MobileElementCommonHelper.findElement(to, timeout)
			if (element != null) {
				KeywordUtil.markPassed("Object " + to.getObjectId() + " is present")
			}
			return true
		} catch (Exception e) {
			KeywordUtil.markFailed("Object " + to.getObjectId() + " is not present")
		}
		return false;
	}

	/**
	 * Get mobile driver for current session
	 * @return mobile driver for current session
	 */
	@Keyword
	def WebDriver getCurrentSessionMobileDriver() {
		return MobileDriverFactory.getDriver();
	}

	/**
	 * Send request and verify status code
	 * @param request request object, must be an instance of RequestObject
	 * @param expectedStatusCode
	 * @return a boolean to indicate whether the response status code equals the expected one
	 */
	@Keyword
	def verifyStatusCode(TestObject request, int expectedStatusCode) {
		if (request instanceof RequestObject) {
			RequestObject requestObject = (RequestObject) request
			ResponseObject response = WSBuiltInKeywords.sendRequest(requestObject)
			if (response.getStatusCode() == expectedStatusCode) {
				KeywordUtil.markPassed("Response status codes match")
			} else {
				KeywordUtil.markFailed("Response status code not match. Expected: " +
						expectedStatusCode + " - Actual: " + response.getStatusCode() )
			}
		} else {
			KeywordUtil.markFailed(request.getObjectId() + " is not a RequestObject")
		}
	}
	
	/**
	 * if a key is given make an object of objects by this data column key, otherwise make it an object of an array for each line
	 * E.g. use method like such Map propertiesJSON = sampleKeywords.toJSONByKey(findTestData('Other/properties'),'env')
	 * @param TestData
	 * @param String
	 * @return
	 */
	@Keyword
	def toJSONByKey(TestData data,String key=null){
		String []columnNames = data.getColumnNames()
		JsonSlurper slurper = new JsonSlurper()

		Map dataJSON = key == null ? [:] : slurper.parseText('{}')

		for (def index : (1..data.getRowNumbers())){
			dataJSON[key == null ? index-1 : data.getValue(key, index)]=slurper.parseText('{}')
			for (def col : (1..data.getColumnNumbers())) {
				String columnName = columnNames[col-1]
				String cellValue = data.getValue(col,index).trim()
				dataJSON[key == null ? index-1 : data.getValue(key, index)][columnName]=cellValue
			}
		}
		return dataJSON
	}


	/**
	 * Add Header basic authorization field,
	 * this field value is Base64 encoded token from user name and password
	 * @param request object, must be an instance of RequestObject
	 * @param username username
	 * @param password password
	 * @return the original request object with basic authorization header field added
	 */
	@Keyword
	def addBasicAuthorizationProperty(TestObject request, String username, String password) {
		if (request instanceof RequestObject) {
			String authorizationValue = username + ":" + password
			authorizationValue = "Basic " + authorizationValue.bytes.encodeBase64().toString()

			// Find available basic authorization field and change its value to the new one, if any
			List<TestObjectProperty> headerProperties = request.getHttpHeaderProperties()
			boolean fieldExist = false
			for (int i = 0; i < headerProperties.size(); i++) {
				TestObjectProperty headerField = headerProperties.get(i)
				if (headerField.getName().equals('Authorization')) {
					KeywordUtil.logInfo("Found existent basic authorization field. Replacing its value.")
					headerField.setValue(authorizationValue)
					fieldExist = true
					break
				}
			}

			if (!fieldExist) {
				TestObjectProperty authorizationProperty = new TestObjectProperty("Authorization",
						ConditionType.EQUALS, authorizationValue, true)
				headerProperties.add(authorizationProperty)
			}
			KeywordUtil.markPassed("Basic authorization field has been added to request header")
		} else {
			KeywordUtil.markFailed(request.getObjectId() + "is not a RequestObject")
		}
		return request
	}


}
```

![](https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/sample-custom-keywords/Screen-Shot-2018-03-26-at-13.36.40.png)
