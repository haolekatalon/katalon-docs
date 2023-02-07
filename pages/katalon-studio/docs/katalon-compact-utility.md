---
title: "Katalon Compact Utility" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/katalon-compact-utility.html 
redirect_from:
description: 
---

> Requirements:
>
> * For Chrome: Katalon Studio version 8.2.5 onwards.
> * For Microsoft Edge: Katalon Studio version 8.3.5 onwards.
> * A Chrome or Microsoft Edge Profile. Find more information at Google Help Center: [Share Chrome with others](https://support.google.com/chrome/answer/2364824/share-chrome-with-others-computer), and Microsoft Support: [Sign in and create multiple profiles in Microsoft Edge](https://support.microsoft.com/en-us/topic/sign-in-and-create-multiple-profiles-in-microsoft-edge-df94e622-2061-49ae-ad1d-6f0e43ce6435).

In restricted environments, unpacked extensions are disabled as a security feature. In that case, using the Spy, Record, and Smart Wait with Chrome might prompt this error: "_Loading the unpacked extension is disabled by the administrators_."

It is possible to use the packed extension **Katalon Compact Utility** as an alternative. The extension is available on Chrome Web Store and Microsoft Edge Add-ons.

This article shows you how to install the extension, configure your Profile, and use the Spy, Record, and Smart Wait in Katalon Studio.

> Notes:
>
> This utility is associated with your Chrome/ Microsoft Edge Profile, which means you can only have one active session at any given time.
>
> Hence, before executing, make sure you log out of all your Chrome/ Microsoft Edge sessions.

## Installing Katalon Compact Utility

1. Open Chrome/ Microsoft Edge. Make sure you use the Profile you want to use the Spy, Record, or Smart Wait with.

2. Navigate to the extension page:

	* Chrome Web Store: [Katalon Compact Utility](https://chrome.google.com/webstore/detail/kataton-compact-utility/gkihajmjffefinkmpokfepcdbhnpflee?hl=en&authuser=1).
	* Microsoft Edge Add-ons: [Katalon Compact Utility](https://microsoftedge.microsoft.com/addons/detail/katalon-compact-utility/kkmafoknllgdaapbegpkpmbncidodkaa).

3. Download and install **Katalon Compact Utility**.

4. Make sure the extension is now active. You can find instructions to manage your extensions here:

	* For Chrome: [Install and Manage Extensions](https://support.google.com/chrome_webstore/answer/2664769).
	* For Microsoft Edge: [Find, add, or remove extensions in Microsoft Edge](https://support.microsoft.com/en-us/microsoft-edge/find-add-or-remove-extensions-in-microsoft-edge-f3522273-d067-7435-6a9d-fdb99213e9a8).

## Configuring and Using the Compact Utility with Chrome Profile

The next steps help you associate your Chrome Profile with the Spy, Record, and Smart Wait functions in Katalon Studio.

To configure and use Katalon Compact Utility, you need to update the Desired Capabilities. Do as follows:

1. Go to **Project > Settings > Desired Capabilities**.
2. In the **Desired Capabilities** section, select **Web UI > Chrome**.
3. Click **Add** to create a new capability named `args`, for which the type is `List`.
4. To add elements to your list, in the **Value** column of the capability you've created, click on the `...` button.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/katalon-compact-utility/project-settings-825.png" alt="element" width=85%>

5. The **List Properties Builder** dialog appears. Click **Add** to create two elements as below. When you are done, click **OK** to save.

	<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/katalon-compact-utility/list-properties-builder.png" alt="list" width=85%>
    
<table>
	<tbody>
		<tr>
			<td><strong>Type</strong></td>
			<td><strong>Value</strong></td>
		</tr>
		<tr>
			<td rowspan="2">String<br /><br /></td>
			<td>For Windows:&nbsp;<code>user-data-dir=C:/Users/&lt;your_username&gt;/Desktop/User Data</code></td>
		</tr>
		<tr>
			<td>For Mac OS:&nbsp;<code>user-data-dir=/Users/&lt;your_username&gt;/Library/Application Support/Google/Chrome</code></td>
		</tr>
		<tr>
			<td>String</td>
			<td><code>profile-directory=&lt;your_profile_name&gt;</code></td>
		</tr>
	</tbody>
</table>

> **Finding your Chrome Profile in the User Data Directory**
>
> There are multiple Profiles in a given User Data Directory. To find the name of a Chrome Profile, do as follows:
>
> * Open Chrome with the Profile you previously used to install Katalon Compact Utility. In the address bar, type `chrome://version` and press Enter.
> * The line **Profile Path** displays the path to your active Profile. For example: `C:\Users\your_username\AppData\Local\Google\Chrome\User Data\your_profile_name`.

6. To save the Chrome configuration, click **Apply and Close**. 

	You can now use the Spy, Record, and Smart Wait features with the default Chrome option.

## Configuring and Using the Compact Utility with Microsoft Edge Profile

The next steps help you associate your Microsoft Edge Profile with the Spy, Record, and Smart Wait functions in Katalon Studio.

To configure and use Katalon Compact Utility, you need to update the Desired Capabilities. Do as follows:

1. Go to **Project > Settings > Desired Capabilities**.
2. In the **Desired Capabilities** section, select **Web UI > Edge Chromium**.
3. Click **Add** to create a new capability:

	<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/katalon-compact-utility/edge-desired-capabilities.png" alt="edge-desired-capabilities" width="100%">
	
	- Name: `ms:edgeOptions`
	- Type: `Dictionary`
	- Value: Click on the `...` button of the value cell, the **Dictionary Properties Builder** dialog appears. Click **Add** and input these fields:

		<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/katalon-compact-utility/dictionary-properties-builder.png" alt="add dictionary" width="100%">

		- Name: `args`
		- Type: `List`
		- Value: Click on the `...` button of the value cell, the **List Properties Builder** dialog appears.

			<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/katalon-compact-utility/edge-list-properties-builder.png" alt="list" width=100%>

			Click **Add** to create two elements as below. When you are done, click **OK** to save.
    
<table>
	<tbody>
		<tr>
			<td><strong>Type</strong></td>
			<td><strong>Value</strong></td>
		</tr>
		<tr>
			<td rowspan="2">String<br /><br /></td>
			<td>For Windows: <code>user-data-dir=C:/Users/&lt;your_username&gt;/Desktop/User Data</code></td>
		</tr>
		<tr>
			<td>For Mac OS: <code>user-data-dir=/Users/&lt;your_username&gt;/Library/Application Support/Microsoft Edge</code></td>
		</tr>
		<tr>
			<td>String</td>
			<td><code>profile-directory=&lt;your_profile_name&gt;</code></td>
		</tr>
	</tbody>
</table>

> **Finding your Microsoft Edge Profile in the User Data Directory**
>
> There are multiple Profiles in a given User Data Directory. To find the name of a Microsoft Edge Profile, do as follows:
>
> * Open Microsoft Edge with the Profile you previously used to install Katalon Compact Utility. In the address bar, type `edge://version` and press Enter.
> * The line **Profile Path** displays the path to your active Profile. For example: `/Users/your_username/Library/Application Support/Microsoft Edge/Default`.

4. To save the configuration, click **Apply and Close**. 

	You can now use the Spy, Record, and Smart Wait features with the default Microsoft Edge option.

### Disable XPath visibility

From Katalon Studio version 8.2.5 onwards, you can enable/disable the XPath visibility while recording actions on your app under test. Do as follows:

1. For Chrome: Open Chrome, then click on the *Extension* icon. Click on the *More* icon of the **Katalon Compact Utility**, then choose **Options**.

	For Microsoft Edge: Open Microsoft Edge, then click on the *More* icon and choose **Extension > Manage Extension**. Click on **Details** of the **Katalon Compact Utility**.
2. Click on the **XPath Visibility** toggle to enable/disable XPath visibility.

	<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/katalon-compact-utility/xpath-visibility.png" alt="xpath visibility" width=60%>

> Known limitation:
>
> * For web pages saved as HTML local files, Katalon Compact Utility cannot spy and capture objects, while unpacked extensions (from the native Spy and Record utility) can do that.

See also:

* [Spy Web Utility](https://docs.katalon.com/katalon-studio/docs/spy-web-utility.html)
* [Creating test cases using Record & Playback](https://docs.katalon.com/katalon-studio/docs/create_test_case_using_record_playback.html)
* [[WebUI] Smart Wait Function](https://docs.katalon.com/katalon-studio/docs/webui-smartwait.html)
