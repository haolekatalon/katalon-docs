---
title: "Sauce Labs Integration" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/saucelabs-plugin.html
redirect_from:
    - "/katalon-studio/docs/saucelabs-integration.html"
    - "/display/KD/SauceLabs+Integration/"
    - "/display/KD/SauceLabs%20Integration/"
    - "/x/UBVO/"
    - "/katalon-studio/docs/saucelabs-integration/"
description: Guide to use the plugin to integrate Katalon Studio with Sauce Labs.
---

> Requirements:
> * An active Katalon Studio Enteprise license. To learn more about activating your license, you can refer to this document: [Activate Katalon license](https://docs.katalon.com/katalon-studio/docs/activate-license.html).

## Install the Sauce Labs Integration plugin

Download and install the **Sauce Labs Integration** plugin. You can download the plugin from the Katalon Store here: [Sauce Labs Integration](https://store.katalon.com/product/75/Sauce-Labs-Integration#pricing-content).

To activate the plugin, navigate to Account Settings in Katalon Studio and click **Reload Plugin**.
## Sauce Labs for WebUI testing
### Create a default Sauce Labs custom profile from the plugin

Go to **Project > Settings > Plugins > Sauce Labs Integration**. Enter your credentials and your desired Sauce Labs operating environments and systems, including: 

<table>
<thead>
  <tr>
    <th>Information</th>
    <th>Description</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>API Key</td>
    <td>An API Key is the Access Key generated from the User Settings in Sauce Labs. You can refer to this Sauce Labs document for further details about retrieving the API key: <a href="https://docs.saucelabs.com/basics/acct-team-mgmt/managing-user-info/#user-settings" target="_blank" rel="noopener noreferrer">User Settings</a>.</td>
  </tr>
  <tr>
    <td>Username</td>
    <td>Your username displayed in Sauce Labs. You can retrieve the Sauce Labs username in the User Settings.</td>
  </tr>
  <tr>
    <td>Browser's name</td>
    <td>The execution browser you want to execute with. For example, Safari.</td>
  </tr>
  <tr>
    <td>Platform</td>
    <td>The operating system you want to execute with. For example, macOS 10.13</td>
  </tr>
  <tr>
    <td>Version</td>
    <td>The browser version you want to execute with. For example, you want to run with Safari 11.1, input <code>11.1</code>.</td>
  </tr>
  <tr>
    <td>Job's Name</td>
    <td>The test case name you want to present in Sauce Labs. By default, this is set to <strong>Default Job</strong>.</td>
  </tr>
</tbody>
</table>

Click **Generate Sauce Labs Custom Profile** to finalize your profile. 

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/saucelabs-plugin/KS-SAUCELABS-Enable-saucelabs-integration.png" width="70%" alt="Enable Sauce Labs integration">

To view the newly created custom profile, go to **Projects > Settings > Desired Capabilities > Custom**.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/saucelabs-plugin/KS-SAUCELABS-View-custom-saucelabs-profiles.png" width="70%" alt="View Sauce Labs custom profile">


> Notes: 
> * The default custom profile is named `saucelabs_default`. 

> Known issues:
> * You can only edit the default custom profile properties from the **Sauce Labs Integration** generator in **Project > Settings > Plugins > **Sauce Labs Integration**.

### Create a Sauce Labs custom profile using custom desired capabilities

You can also create a new Sauce Labs custom profile using custom desired capabilities. To do so:

1. Go to **Projects > Settings > Desired Capabilities > Custom**.

2. Click **Add**, then name the new custom profile with the following syntax: `saucelabs_<your-custom-profile-name>`. Here, we name our profile `saucelabs_custom`.

3. Click on *More* (...) under the **Value** column. In the **Custom Execution Configuration Builder** dialog, click **Add**, then choose **Remote**.

4. Click on *More* (...) under the **Preferences** column. In the pop-up **Driver Builder** dialog, specify as follows:

  - **Remote server URL**: specify the Driver Creation URL in Sauce Labs. To find the Driver Creation URL, open your Sauce Labs account, go to **Account** > **User settings**, then scroll to the **Driver Creation** section.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/saucelabs-plugin/KS-SAUCELABS-Driver-URL.png" width="100%" alt="Add Sauce Labs custom profile via desired capabilities">

  - **Remote server type**: choose **Selenium**.

  - Specify your Sauce Labs `username`, `accessKey`.
  - Add other properties for your execution environment. You can refer to the Sauce Labs platform configuration here: [Platform configuration](https://saucelabs.com/platform/platform-configurator).

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/saucelabs-plugin/KS-SAUCELABS-Desired-capabilities.png" width="70%" alt="Add Sauce Labs custom profile via desired capabilities">`

  You can now use the newly created profile to execute tests.
### Execute a test case with Sauce Labs profiles

To execute a test case with Sauce Labs profiles, do as follows:

1. Open a test case.

2. Click the dropdown list next to **Run**.

3. Select **Custom capabilities**.

4. Select your Sauce Labs profile.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/saucelabs-plugin/830-KS-SAUCELABS-Execute-test-case-saucelabs-profile.png" width="100%" alt="Execute Sauce Labs custom profile in a test case">

### Execute a test suite with Sauce Labs profiles

To execute a test suite with Sauce Labs profiles, do as follows:

1. Open a test suite.

2. Add the test cases you want to execute into the test suite.

3. Click the dropdown list next to **Run**.

4. Select **Custom capabilities**.

5. Select your Sauce Labs profile.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/saucelabs-plugin/KS-SAUCELABS-Execute-test-suite-saucelabs-profile.png" width="100%" alt="Execute Sauce Labs custom profile in a test suite">

### Execute a test suite collection with Sauce Labs profiles

To execute a test suite collection with Sauce Labs profiles, do as follows:

1. Open a test suite collection.

2. Add the test suites you want to execute into the test suite collection. 

3. Double-click on the cell under the **Run with** column. A **Select an environment** dialog opens.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/saucelabs-plugin/KS-SAUCELABS-Select-environment-test-suite-collection.png" width="60%" alt="Choose Sauce Labs custom profile in a test suite collection">

4. Select your Sauce Labs profile.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/saucelabs-plugin/KS-SAUCELABS-Select-environment-TSC.gif" width="100%" alt="Choose Sauce Labs custom profile in a test suite collection">

5. Click **OK**. Then click **Execute**.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/saucelabs-plugin/KS-SAUCELABS-Execute-test-suite-collection-saucelabs-profile.png" width="100%" alt="Execute Sauce Labs custom profile in a test suite collection">

### View test execution results on Sauce Labs

To view Katalon test execution results on Sauce Labs, on the Sauce Labs Dashboard, switch to the **Automated > Test Results** tab.

You can see the test results displayed as follows: 

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/saucelabs-plugin/KS-SAUCELABS-Uploaded-test-results.png" width="100%" alt="View test execution results in Sauce Labs">


> Notes:
> * If you are running with the `saucelabs_default` profile, your test result is uploaded to the **US West 1** data center.
> * Make sure to select the correct data center that you specify in the **Remote server URL** of your Sauce Labs custom profile.
> <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/saucelabs-plugin/KS-SAUCELABS-data-center.png" width="30%" alt="Select data center">

## Sauce Labs for mobile testing and hybrid application testing

To enable mobile and hybrid application testing with Sauce Labs profiles, you need to manually add capabilities in **Projects > Settings > Desired Capabilities > Custom**.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/saucelabs-plugin/KS-SAUCELABS-Add-saucelabs-profile-mobile-testing.png" width="70%" alt="Add custom profile for mobile testing">

Then add mobile and hybrid application testing capabilities in the Sauce Labs document here: [Appium Testing with Real Devices](https://docs.saucelabs.com/mobile-apps/automated-testing/appium/real-devices/).
