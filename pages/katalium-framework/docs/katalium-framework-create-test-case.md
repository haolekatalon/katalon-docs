---
title: "Create a Test Case" 
sidebar: katalon_studio_docs_sidebar
permalink: katalium-framework/docs/katalium-framework-create-test-case.html
description:
---

Test cases are essentially TestNG's test classes. Katalium Framework provides an abstract class `com.katalon.kata.testng.TestTemplate` with some convenient utilities:

* WebDriver is initialized before each test method and can be accessed with `this.driver` or `driver`. If the test method ends with a `driver.quit()` statement, a new WebDriver will be created for the next test method.

* Page instances are also preinitialized using Selenium's `PageFactory`. Refer to [this article](/katalium-framework/docs/katalium-framework-page-object-model.html) to learn more about the Page Object Model.

Here is a very simple Selenium test ([source code](https://github.com/katalon-studio/katalium-sample/blob/master/src/test/java/com/katalon/kata/sample/testcase/simple/LoginTest.java)):

```java
package com.katalon.kata.sample.testcase.simple;

import com.katalon.kata.sample.Constants;
import com.katalon.kata.sample.page.CuraAppoinmentPage;
import com.katalon.kata.sample.page.CuraHomePage;
import com.katalon.kata.sample.page.CuraLoginPage;
import com.katalon.kata.testng.TestTemplate;
import org.testng.Assert;
import org.testng.annotations.Test;

public class LoginTest extends TestTemplate {

  private CuraHomePage curaHomePage = new CuraHomePage(Constants.baseUrl);

  private CuraLoginPage curaLoginPage;

  private CuraAppoinmentPage curaAppoinmentPage;

  @Test
  public void shouldLogin() {
    curaHomePage.open();
    curaHomePage.makeAppointment();
    curaLoginPage.login(Constants.username, Constants.password);
    boolean exist = curaAppoinmentPage.isOnPage();
    Assert.assertTrue(exist);
    driver.quit();
  }
}
```