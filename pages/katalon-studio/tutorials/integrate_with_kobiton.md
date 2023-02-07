---
title: "Mobile Testing with Kobiton Devices"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/integrate_with_kobiton.html
description: "Using Katalon Studio, you can easily execute automated tests on Kobiton’s devices, thanks to the built-in integration feature supported by Katalon Studio."
redirect_from:
    - "/katalon-studio/tutorials/integrate_with_kobiton.html"
    - "/katalon-studio/docs/desired-capabilities-for-kobiton-devices.html"
    - "/display/KD/Desired+Capabilities+for+Kobiton+Devices/"
    - "/display/KD/Desired%20Capabilities%20for%20Kobiton%20Devices/"
    - "/x/DQrR/"
    - "/katalon-studio/docs/desired-capabilities-for-kobiton-devices/"
    - "/display/KD/Desired+capabilities+for+Kobiton+devices/"
    - "/katalon-studio/docs/use-additional-desired-capabilities-for-kobiton-devices.html/"
    - "/katalon-studio/docs/enable-kobiton-integration.html"
    - "/display/KD/Enable+Kobiton+Integration/"
    - "/display/KD/Enable%20Kobiton%20Integration/"
    - "/display/KD/Kobiton+Integration/"
    - "/display/KD/Kobiton%20Integration/"
    - "/x/7IEw/"
    - "/katalon-studio/docs/enable-kobiton-integration/"
---

> From version 7.8 onwards, Kobiton accounts using SAML SSO login method can integrate with Katalon Studio. See Kobiton documentation on [Configuring Single Sign-On/SSO and SAML with Kobiton](https://support.kobiton.com/hc/en-us/articles/4404857846157-Configuring-Single-Sign-On-SSO-and-SAML-with-Kobiton)

## Enable Kobiton Integration

Kobiton is a mobile device platform that offers real mobile devices for both testers and developers. Using Katalon Studio, you can execute automated tests on Kobiton's devices. To enable Kobiton Integration, follow these steps:

1. Install the [Kobiton Integration](https://store.katalon.com/product/137/Kobiton-Integration) plugin from Katalon Store. After installing the plugin, open **Katalon Studio > your Account > Reload Plugins**. You can refer to the section [Reload Plugins](https://docs.katalon.com/katalon-store/docs/user/access-store-in-KS.html#reload-plugins) for detailed instructions.

2. Open Kobiton integration settings from the main menu:

* Windows: **Windows > Katalon Studio Preferences > Katalon > Kobiton**.
* macOS: **Katalon Studio > Preferences > Katalon > Kobiton**.

3. Select **Enable Kobiton Integration** and authenticate your access to the Kobiton Server.

* From version **7.8.0 onwards**: enter you username and API Key, then click **Test Connection**.
   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/enable-kobiton-integration/sso-kobiton.png" alt="enable kobiton integration 7.8 onwards" width=70%>

   * **Kobiton Server**: The Kobiton server to be integrated with Katalon Studio.
        > From version **8.1.0 onwards**, you can customize the remote server protocol and pathname. Katalon Studio uses HTTP protocol by default. If your environment prevents sending basic authentication credentials through HTTP, you can input a remote URL with HTTPS instead.
   * **API Key**: The token to be used by Katalon Studio when exchanging API messages with Kobiton server. You can generate more keys in [Kobiton API Settings](https://portal.kobiton.com/settings/keys).

* Prior to version 7.8.0, enter your Kobiton account in the **Authentication** form and click **Connect**. Katalon Studio retrieves the information for Kobiton integration automatically.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/enable-kobiton-integration/image2017-6-29-163A543A3.png" alt="enable kobiton integration before 7.8" width=70%>
  
4. When you are done with the configuration, click **Apply and close**.

## Desired Capabilities for Kobiton Devices

> **Prerequisites**
>
> Kobiton integration is enabled, and you have adjusted your existing test scripts accordingly. Refer to [Enable Kobiton Integration](https://docs.katalon.com/katalon-studio/docs/enable-kobiton-integration.html) for more details.

You can add additional desired capabilities for Kobiton devices, such as using the `appWaitActivity` capability to troubleshoot an issue related to starting an application. See [Troubleshooting automated mobile testing](https://docs.katalon.com/katalon-studio/docs/troubleshooting-automated-mobile-testing.html).

1. Copy the [desired capabilities](https://docs.kobiton.com/automation-testing/automation-testing-with-kobiton/): In the Kobiton portal, select the device you want to use. Click **Automation setting** and copy the desired capabilities.
Open Katalon Studio, then paste these desired capabilities to your test script. 
<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/desired-capabilities-for-kobiton-devices/Screen-Shot-2018-07-05-at-11.40.52.png" alt="grab desired capabilities" width=70%>

2. Insert '**app**' capability and pass in Kobiton application id for your device, e.g.,

    ```groovy
    String kobitonServerUrl = "https://katalon-integration:xxxxxxxxxxxxxxxxxxx@api.kobiton.com/wd/hub";
    DesiredCapabilities capabilities = new DesiredCapabilities();
    capabilities.setCapability("sessionName", "Automation test session");
    capabilities.setCapability("sessionDescription", ""); 
    capabilities.setCapability("deviceOrientation", "portrait");  
    capabilities.setCapability("captureScreenshots", true); 
    capabilities.setCapability("browserName", "chrome"); 
    capabilities.setCapability("deviceGroup", "KOBITON"); 
    capabilities.setCapability("deviceName", "Galaxy J3(2016)");
    capabilities.setCapability("platformVersion", "6.0.1");
    capabilities.setCapability("platformName", "Android"); 
    capabilities.setCapability('app', 'kobiton-store:10717');
    ```

    3\. **Replace** 'Start Application' keyword with these lines. These codes will establish a connection to selected Kobiton's device and also create a driver to be used for other built-in keywords. Thus, you don't have to rewrite the whole test script again.

    ```groovy
    import static com.kms.katalon.core.testobject.ObjectRepository.findTestObject
    import org.openqa.selenium.remote.DesiredCapabilities
    import com.kms.katalon.core.appium.driver.AppiumDriverManager
    import com.kms.katalon.core.configuration.RunConfiguration as RunConfiguration
    import com.kms.katalon.core.mobile.driver.MobileDriverType
    import com.kms.katalon.core.mobile.keyword.MobileBuiltInKeywords as Mobile
    import com.kms.katalon.core.util.internal.PathUtil as PathUtil
    import internal.GlobalVariable as GlobalVariable
    import io.appium.java_client.android.AndroidDriver
    
    //Mobile.startApplication('kobiton-store:10717', false)
    String kobitonServerUrl = "https://katalon-integration:xxxxxxxxxxxxxxx@api.kobiton.com/wd/hub";
    DesiredCapabilities capabilities = new DesiredCapabilities();
    capabilities.setCapability("sessionName", "Automation test session");
    capabilities.setCapability("sessionDescription", ""); 
    capabilities.setCapability("deviceOrientation", "portrait");  
    capabilities.setCapability("captureScreenshots", true); 
    capabilities.setCapability("browserName", "chrome"); 
    capabilities.setCapability("deviceGroup", "KOBITON"); 
    capabilities.setCapability("deviceName", "Galaxy J3(2016)");
    capabilities.setCapability("platformVersion", "6.0.1");
    capabilities.setCapability("platformName", "Android"); 
    capabilities.setCapability('app', 'kobiton-store:10717')
    
    AppiumDriverManager.createMobileDriver(MobileDriverType.ANDROID_DRIVER, capabilities, new URL(kobitonServerUrl))
    ```

    _If you use an iOS device, then please change MobileDriverType.ANDROID\_DRIVER to MobileDriverType.IOS\_DRIVER._  
      
    Now you've finished adjusting the 'Start Application' keyword. Here is the complete code:
    
    ```groovy
    import static com.kms.katalon.core.testobject.ObjectRepository.findTestObject
    import org.openqa.selenium.remote.DesiredCapabilities
    import com.kms.katalon.core.appium.driver.AppiumDriverManager
    import com.kms.katalon.core.configuration.RunConfiguration as RunConfiguration
    import com.kms.katalon.core.mobile.driver.MobileDriverType
    import com.kms.katalon.core.mobile.keyword.MobileBuiltInKeywords as Mobile
    import com.kms.katalon.core.util.internal.PathUtil as PathUtil
    import internal.GlobalVariable as GlobalVariable
    import io.appium.java_client.android.AndroidDriver
    
    'Instead of using Start Application keyword, we use the below code to create a similar driver so that other Mobile built-in keywords can re-use this driver.'
    String kobitonServerUrl = "https://katalon-integration:xxxxxxxxx@api.kobiton.com/wd/hub";
    DesiredCapabilities capabilities = new DesiredCapabilities();
    capabilities.setCapability("sessionName", "Automation test session");
    capabilities.setCapability("sessionDescription", ""); 
    capabilities.setCapability("deviceOrientation", "portrait");  
    capabilities.setCapability("captureScreenshots", true); 
    capabilities.setCapability("browserName", "chrome"); 
    capabilities.setCapability("deviceGroup", "KOBITON"); 
    capabilities.setCapability("deviceName", "Galaxy J3(2016)");
    capabilities.setCapability("platformVersion", "6.0.1");
    capabilities.setCapability("platformName", "Android"); 
    capabilities.setCapability('app', 'kobiton-store:10717')
    AppiumDriverManager.createMobileDriver(MobileDriverType.ANDROID_DRIVER, capabilities, new URL(kobitonServerUrl))
    
    Mobile.tap(findTestObject('Application/android.widget.TextView - App'), 10)
    
    Mobile.tap(findTestObject('Application/App/android.widget.TextView-Activity'), 10)
    
    Mobile.tap(findTestObject('Application/App/Activity/android.widget.TextView-Custom Dialog'), 10)
    
    'Get displayed message on the dialog'
    def message = Mobile.getText(findTestObject('Application/App/Activity/Custom Dialog/android.widget.TextViewCustomDialog'), 
        10)
    
    Mobile.comment('Then the correct dialog message should be displayed')
    
    Mobile.verifyEqual(message, 'Example of how you can use a custom Theme.Dialog theme to make an activity that looks like a customized dialog, here with an ugly frame.')
    
    Mobile.closeApplication()
    ```
## Mobile Testing with Kobiton Devices

Install and enable the Kobiton Integration plugin. If you haven't configured the integration yet, refer to this section: [Enable Kobiton Integration](https://docs.katalon.com/katalon-studio/docs/enable-kobiton-integration.html) for instructions.

To do this, follow the instructions below to execute your Katalon Studio automation test with Kobiton mobile devices.

1\. Navigate to [Kobiton Portal](https://portal.kobiton.com) and log in with your Kobiton username and password.

2\. In Kobiton, upload your app to the Kobiton App Repository. See Kobiton documentation on [Managing Applications](https://support.kobiton.com/hc/en-us/articles/360056028911-Managing-Applications-).

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/tutorials/integrate_with_kobiton/add-app.png" width="100%">

3\. From the Repository view, click on the drop-down icon on the right corner. Copy the app ID to your clipboard for later use (for example, **2229394** as shown below).

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/tutorials/integrate_with_kobiton/app-ID.png" width=70%>

4\. Click on the **Devices** menu. Select your device, then click on the _flag_ in the top right corner to **Mark as favorite**.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/tutorials/integrate_with_kobiton/mark-as-favourite.png" width=70%>

> From **version 8.1.0 onwards**, you can change Kobiton's **Custom Device Name** to select the correct device on Katalon Studio. If your Kobiton devices don't have any custom name, Katalon Studio uses the devices' original name when running tests. See Kobiton documentation on [Device Custom Name](https://support.kobiton.com/hc/en-us/articles/360055588512-Device-Custom-Name-)

Once you have set your Device Custom Names in Kobiton Portal, you can check the Kobiton devices list in Katalon Studio. Go to Katalon Studio, then open **Mobile Recorder/Spy > Select Kobiton Device**.

5\. In Katalon Studio, open your mobile test case and switch to the **Scripts** view. Locate this line of code:

```groovy
Mobile.startApplication(appPath,false).

```

Next, replace the `appPath` with the Kobiton **App ID** saved in Step 3, as shown below:

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/tutorials/integrate_with_kobiton/Kobiton-app-id.png" alt="replace the appPath with the Kobiton app id" width=100%>

```groovy
import static com.kms.katalon.core.testcase.TestCaseFactory.findTestCaseMobile.comment('Story: Verify correct alarm message')Mobile.comment('Given that user has started an application')'Get full directory\'s path of android application'

//def appPath = PathUtil.relativeToAbsolutePath(GlobalVariable.G_AndroidApp, RunConfiguration.getProjectDir())

Mobile.startApplication('kobiton-store:184', false)

Mobile.comment('And he navigates the application to Activity form')

Mobile.tap(findTestObject('Application/android.widget.TextView - App'), 10)

Mobile.tap(findTestObject('Application/App/android.widget.TextView-Activity'), 10)

Mobile.comment('When he taps on the Custom Dialog button')

Mobile.tap(findTestObject('Application/App/Activity/android.widget.TextView-Custom Dialog'), 10)

'Get displayed message on the dialog'

def message = Mobile.getText(findTestObject('Application/App/Activity/Custom Dialog/android.widget.TextViewCustomDialog'),10)

Mobile.comment('Then the correct dialog message should be displayed')

Mobile.verifyEqual(message, 'Example of how you can use a custom Theme.Dialog theme to make an activity that looks like a customized dialog, here with an ugly frame.')

Mobile.closeApplication()

```

6\. From the main toolbar, click on the drop-down menu of **Run**, and select the option to run with **Kobiton Device**.  

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/tutorials/integrate_with_kobiton/Run.png" alt="run with Kobiton Device" width=30%>

7\. On the Kobiton Favorite Devices screen, a list of **Favorite Devices** displays in **Device Name**.  

Select your preferred device and click **Ok**.

>**Notes**:
>
> You can also modify this list by updating your **Favorite Devices** from [Kobiton Portal](https://portal.kobiton.com/devices).


<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/tutorials/integrate_with_kobiton/Favorite-Devices.png" alt="Kobiton Favorite Devices" width=70%>

> To dynamically change Kobiton devices in console mode, see [Integration Options](https://docs.katalon.com/katalon-studio/docs/console-mode-execution.html#integration-options).

8\. Once Katalon Studio finishes configuring, the automated test execution session will be uploaded to Kobiton.

You can view the session in the **Sessions** section in Kobiton.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/tutorials/integrate_with_kobiton/Sessions.png" alt="automation test execution uploaded to Kobiton" width=100%>