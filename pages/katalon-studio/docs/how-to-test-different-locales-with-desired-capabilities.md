---
title: "Test different browser locales in Chrome with Desired Capabilities"
sidebar: katalon_studio_docs_sidebar
permalink: /katalon-studio/docs/test-different-browser-locales-in-chrome-with-desired-capabilities.html
redirect_from:
description:
---

Chrome sets a default UI language with the first Chrome window that opens. In other words, if you alter browser locales, for example, with command line argument `chrome.exe --lang=de` to start Chrome in German, the Chrome driver still defines the default language from the Chrome browser.

To test different browser locales, you can instead configure Desired Capabilities. You can learn about this here: [Desired Capabilities](https://docs.katalon.com/katalon-studio/docs/introduction-to-desired-capabilities.html)

## Use Configured Desired Capability with Test Case Variables

In this section, we show you two possible approaches to alter browser locales while testing: 

- To test one specific language with a test case.
- To test different languages with a test suite.

> Here is a sample project you can download as a .zip file: 
> * [Sample test cases run with multiple locales](https://github.com/katalon-studio-samples/multi-locales-sample/blob/main/Test%20Cases/Run%20with%20local%20Chrome.tc).
> * [Sample test suite with data binding support](https://github.com/katalon-studio-samples/multi-locales-sample/tree/main/Test%20Suites).
### Create a test case to test one language

In the following example, we configure a test case with a specific browser locale, like French.

Do as follows:

1. Create a New Test Case. Go to **File > New > Test Case.**

2. Create Test Case Variables. See also: [Test Case Variables](https://docs.katalon.com/katalon-studio/docs/test-case-variables.html#manage-test-case-variables). 

   - Switch to the Variables tab of your Test Case.
   - Click **Add**. A new row appears in the variable list.
   - Input the "locale" variable like so:

    <table width="959">
    <tbody>
    <tr>
    <td><strong>Name</strong></td>
    <td><strong>Type</strong></td>
    <td><strong>Default Value</strong></td>
    </tr>
    <tr>
    <td>locale</td>
    <td>String</td>
    <td>"fr"</td>
    </tr>
    </tbody>
    </table>
    
   - In our example, the **Default Value** is `fr`, the language code for French. You can find other language codes for Chrome here: [language code](https://developers.google.com/admin-sdk/directory/v1/languages).

      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/how-to-guides/tests-different-browser-locales-with-DC/Test-case-variables-2.png" width=90% alt="test case with variables">


3. After defining Test Case Variables, we override default language settings in Chrome by using Configured Desired Capabilities. You can learn more about this here: [Configured Desired Capabilities](https://docs.katalon.com/katalon-studio/docs/introduction-to-desired-capabilities.html#passing-desired-capabilities-at-runtime)

    - Switch to the Script tab of your Test Case.
    - Copy and paste the below code into your test script. With this code, you can manipulate the locales of the testing browsers.

      ```groovy

      import com.kms.katalon.core.configuration.RunConfiguration

      Map prefs = [('intl.accept_languages') : locale]
      // Map preferences key to manipulate page's language.

      RunConfiguration.setWebDriverPreferencesProperty("prefs", pref)
      ```

    - Continue writing the script or use Web Spy/Record Utility to complete your test case.

      > Notes:
      > 
      > In case you wish to alter browser locales with an existing test script, copy and paste the above sample code before the test script.
      > 

      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/how-to-guides/tests-different-browser-locales-with-DC/configured-desired-capabilities.png" width=90% alt="Final results after configuring Desired Capabilities">

    - Your Test Case is now ready to run with Chrome in French.

### Create a Test Suite to test different languages

> Requirements:
> 
> * Make sure to configure all your test cases with Desired Capabilities as per Part 1. 
>
>

> Notes:
> * Desired Capabilities can be reused across projects. You can refer to this document: [Reuse Desired Capabilities](https://docs.katalon.com/katalon-studio/docs/import-export-desired-capabilities.html) for further details.

In the following example, we demonstrate how to create a Test Suite with Test case variables to test different browser locales. Here, we use French, English, and Spanish.

1. Create a test suite. Go to **File > New > Test Suite.**
2. Click **Add** in the command toolbar, then choose pre-configured test cases.

    <img src="https://github.com/katalon-studio/docs-images/raw/d22b289b2b07c6ae15b9a52e11a3cc245e725974/katalon-studio/how-to-guides/tests-different-browser-locales-with-DC/new-test-suite.png" width=70% alt="New Test Suite">

3. Create a data file. Go to **File > New > Test Data.** Choose **Data Type** as **Internal Data.**

    You use this data file to input different language codes you want to test on browsers. For our example, we input `fr`,`en`,`es`.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/how-to-guides/tests-different-browser-locales-with-DC/create-new-data-file-2.png" width=70% alt="New Data file 2">

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/how-to-guides/tests-different-browser-locales-with-DC/New%20Data%20File.png" width=70% alt="New Data file">

4. Manage Data Binding
   
   - Return to your test suite, click **Show Data Binding** to expand the **Data Binding** section. Make sure you click on the correct pre-configured test case beforehand. 

      This step binds the New Data File from Step 3 with the Test Suite you want to run. See also [Manage Data Binding](https://docs.katalon.com/katalon-studio/docs/run-test-case-external-data.html#manage-data-binding).

      <a class="pop">
      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/how-to-guides/tests-different-browser-locales-with-DC/show-data-variables.png" width=70% alt="Show Data Binding section">
      </a>
      <p style="text-align: center;"><em>Click the image to enlarge it</em></p>
      
   - The final results should show as below:
     
      <a class="pop">
      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/how-to-guides/tests-different-browser-locales-with-DC/Test%20Suite%20Data%20Binding.png" width=70% alt="Test Suite data">
      </a>
      <p style="text-align: center;"><em>Click the image to enlarge it</em></p>
## Use Custom Profiles in Desired Capabilities

You can also test different browser locales with a Remote Server. In this case, you can set **Custom Desired Capabilities** to alter the default language in Chrome. 

> Here is a sample project you can download as a .zip file: [Sample test cases with custom execution](https://github.com/katalon-studio-samples/multi-locales-sample/blob/main/Test%20Cases/Run%20with%20custom%20execution.tc).


> Requirements:
> 
> * Make sure that you are running Selenium Grid Hub & Node while executing the test. 
> * Make sure to update the browser by clicking **Tools > Update WebDrivers > Choose browser**. 

The following example shows you how to create a custom profile with Spanish as the testing language.
Do as follows:

1. Create a new Custom profile in **Desired Capabilities**. Go to **Project > Settings > Desired Capabilities > Custom.**

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/project-settings-new-ui/KS-LOCALE-Custom-settings.png" width=70% alt="Project Settings dialog">

2. In the command toolbar, click **Add** to add a custom profile.
  In the newly added property line, change the name to "spanish" for better recognition, then click on *More* (...) under the **Value** column. A **Custom Execution Configuration Builder** dialog opens.
  
    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/project-settings-new-ui/KS-LOCALES-Name-the-property.png" width=70% alt="Set value for custom Desired Capabilities">


3. In the **Custom Execution Configuration Builder** dialog, specify the **Driver Name** as **Remote**, then click on *More* (...) under the **Preferences** column. A **Driver Builder** dialog opens.
 
    <img src="https://github.com/katalon-studio/docs-images/raw/5ce4d691c2e1223380169717503cd3189ae5b1ed/katalon-studio/how-to-guides/tests-different-browser-locales-with-DC/Custom-Execution%20-Configuration%20-Builder-2.jpg" width=70% alt="Set value for custom Desired Capabilities">

  - Fill in the **Driver Builder** dialog as shown below:
    1. Remote Server URL: `http://localhost:port/wd/hub` - the URL to the Remote server.
    2. Remote Server Type: Choose **Selenium**.
    3. Click **Add** on the command toolbar, then input the following values:

      <table>
      <thead>
        <tr>
          <th colspan="3">Table 1</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Name</td>
          <td>Type</td>
          <td>Value</td>
        </tr>
        <tr>
          <td>browserName</td>
          <td>string</td>
          <td>chrome</td>
        </tr>
        <tr>
          <td>goog:chromeOptions(*)</td>
          <td>Dictionary(**)</td>
          <td>Click <em>More</em> (...). In the pop-up <strong>Dictionary Property Builder</strong> dialog, click <strong>Add</strong>, then input values from Table 2.</td>
        </tr>
      </tbody>
      </table>
      
      (*) <em>`goog:chromeOptions`: Support passing the ChromeOptions object into the ChromeDriver constructor.</em>
      
      (**) <em> `Dictionary`: the data type permits you to input a collection of keys and values. You can learn more about this here: [Data types](https://docs.katalon.com/katalon-studio/docs/value-types.html).</em>

      <table>
      <thead>
        <tr>
          <th colspan="3">Table 2</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Name</td>
          <td>Type</td>
          <td>Value</td>
        </tr>
        <tr>
          <td>prefs</td>
          <td>Dictionary</td>
          <td>Click <em>More</em> (...). In the pop-up <strong>Dictionary Property Builder</strong> dialog, click <strong>Add</strong>, then input values from Table 3.</td>
        </tr>
      </tbody>
      </table>

      <table>
      <thead>
        <tr>
          <th colspan="3">Table 3</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Name</td>
          <td>Type</td>
          <td>Value</td>
        </tr>
        <tr>
          <td>intl.accept_languages(*)</td>
          <td>String</td>
          <td>es(**)</td>
        </tr>
      </tbody>
      </table>

      (*) <em>`intl.accept_languages`: Support passing preference key to manipulate a page's language.</em>
      
      (**) <em>`es`: the language code for Spanish.</em>

      <a class="pop">
      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/how-to-guides/tests-different-browser-locales-with-DC/KS-LOCALES-Custom-settings.png" width=70% alt="Set value for custom Desired Capabilities">
      </a>
      <p style="text-align: center;"><em>Click the image to enlarge it</em></p>

      > Notes:
      > * The capabilities properties are case-sensitive.

  4. Click **OK** to save the settings in each table. The above commands should result in the following:

      <a class="pop">
      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/project-settings-new-ui/KS-LOCALE-Final-results.png" width=70% alt="Results after setting up custom language Remote Control dialog">
      </a>
      <p style="text-align: center;"><em>Click the image to enlarge it</em></p>

      <a class="pop">
      <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/how-to-guides/tests-different-browser-locales-with-DC/final-results-3.png" width=70% alt="Final Results"> 
      </a>
      <p style="text-align: center;"><em>Click the image to enlarge it</em></p>


