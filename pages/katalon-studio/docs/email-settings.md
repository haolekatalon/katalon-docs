---
title: "Emails Settings" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/emails-settings.html 
redirect_from:
description: This document shows you how to configure Emails Settings to automatically send summary reports to your email list.
---

After a test suite or test suite collection execution, you might want to automatically send summary reports to your own email or other stakeholders to notify them about the test result. This document shows you how to set up your mail server and customize email reports to automatically send out a summary report email whenever a test execution finishes.

## What you can do in email settings

> From version 7.5.0 onwards, Katalon Studio Enterprise users can send email reports after executing Test Suite Collections.

In Katalon Studio, you can configure a global email settings in **Project > Settings > Email** for the mail server, email template, and report format. You can customize the email template to match the report requirements of your stakeholders and choose which types of report files to be sent as attachments, for example, HTML, CSV, PDF, Log, or PNG.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/execution-settings/KS-Project-Settings-Email.png" alt="Email settings" width=100%>

By default, after you successfully set up your mail server, sender, and recipients, Katalon Studio sends all email reports for test suite executions, including test suites inside a test suite collection.

As an exclusive feature for Katalon Studio Enterprise, you have an option to keep your mailbox tidy by only sending email reports for test suite collection executions and skipping all emails for test suites stored inside that test suite collection. This option is useful when executing test suite collections containing many test suites.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/emails-settings/options.png" width="" alt="Email settings">

## Set up your mail server

**Mail Server Settings** define the mail server Katalon Studio uses for sending emails. To set up your mail server, you need to fill in your mail server host, port, credential, and choose a protocol option.

1. **Host and Port**:

  * **Host**: The domain name of the mail server.
  * **Port**: The port to be used for that server.

  Below is a list of some common outgoing mail (SMTP) server configurations:

<table>
  <thead>
    <tr>
      <th>Email sever</th>
      <th>Host</th>
      <th>Port</th>
      <th>Reference</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Gmail</td>
      <td><a href="http://smtp.gmail.com/">smtp.gmail.com</a></td>
      <td>465 or 587</td>
      <td><a href="https://support.google.com/mail/answer/7126229">Check Gmail through other email platforms</a></td>
    </tr>
    <tr>
      <td>Outlook</td>
      <td><a href="http://smtp.office365.com/">smtp.office365.com</a></td>
      <td>587 or 35</td>
      <td><a href="https://docs.microsoft.com/en-us/exchange/mail-flow-best-practices/how-to-set-up-a-multifunction-device-or-application-to-send-email-using-microsoft-365-or-office-365">How to set up a multifunction device or application to send email using Microsoft 365 or Office 365</a></td>
    </tr>
    <tr>
      <td>Yahoo! Mail</td>
      <td><a href="http://smtp.mail.yahoo.com/">smtp.mail.yahoo.com</a></td>
      <td>465</td>
      <td><a href="https://help.yahoo.com/kb/SLN4724.html">POP access settings and instructions for Yahoo Mail</a></td>
    </tr>
  </tbody>
</table>

2. **Username and Password**:

  * **Username**: Your full email account to authenticate with the server (e.g., yourusername@gmail.com)
  * **Password**: Your email password to authenticate with the server. This could be a password generated from App Passwords.

    For Gmail users:

    * If your email accounts are using two-step authentication, you can use Google App Passwords to set up a Gmail account in Katalon Studio. An App Password is a 16-digit passcode that gives Katalon Studio permission to access your Google Account. In the **Select app** dropdown of App Passwords, select the option **Other (Custom name)** to generate an app password for Katalon Studio. Then, use the generated passwords to put in the password section of **Mail Server Settings**. For details, see Google Account Help documentation: [Sign in with App Passwords](https://support.google.com/accounts/answer/185833).
    * If you do not use two-step authentication, you can allow less secure apps to access your account. However, to help keep your account secure, starting May 30, 2022, ​​Google will no longer support the use of third-party apps or devices which ask you to sign in to your Google Account using only your username and password. For detail, see Google Account Help documentation: [Less secure apps & your Google Account](https://support.google.com/accounts/answer/6010255).

    For Yahoo! Mail, make sure to allow less secure apps to access your account. Follow this guide: [Ways to securely access Yahoo Mail](https://help.yahoo.com/kb/account/SLN27791.html).

    As some SMTP servers do not require authentication and username in email address format, Katalon Studio version 8.3.0 onwards does not validate usernames and passwords.

3. **Protocol**: The protocol to communicate with the mail server. There are three options:

  * None
  * SSL (Secure Sockets Layer)
  * TLS (Transport Layer Security)

4. **Encrypt authentication data**: For sensitive data protection, we recommend enabling **Encrypt authentication data**.

After you fill in your mail server information, you can send a test email to check if the mail server is set up correctly. Input an email in the **Recipients** field, then click **Send Test Email**. The **Send test email** button is only enabled once **Mail Server Settings** and **Recipients** are filled correctly.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/emails-settings/send-test-email.png" alt="send test email" width="100%">

## Email Template

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/execution-settings/KS-Project-Settings-Email-Template-Report-Format.png" alt="Email Template and Report format" width="" height="">

You can define the sender, recipients (the list of emails to receive reports), email subject, and body template in this section.

From version 8.3.0 onwards, Katalon Studio also supports adding Test Suite and Test Suite Collection names in your email subject with the placeholders `${suiteName}` and `${suiteCollectionName}`, respectively.

## Report Format

You can decide whether to include a test execution report as an email attachment or not. Specifically, you are given options to include **log files** and configure which **report format** (HTML, CSV, and PDF) of test executions to be sent as attachments in the email report.

## Body Template

To customize the email's body templates:

For Test Suite's email, click **Edit Template for Test Suite Execution** or go to **Project/Settings/Email/Template/Test Suite**.

  <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/execution-settings/KS-Project-Settings-Email-Test-Suite-Body-Template.png" alt="Test Suite Report email template">

* hostName: Host's name
* os: Operating system
* browser: Browser's name and version
* deviceId: Id of the executed device
* deviceName: Name of the executed device
* suiteId: Id of the test suite
* suiteName: Name of the test suite
* executionProfile: Profile for Test Suite execution
* totalPassed: Total passed test cases
* totalFailed: Total failed test cases
* totalError: Total error test cases

For Test Suite Collection's email, **Edit Template for Test Suite Collection Execution** or go to **Project/Settings/Email/Template/Test Suite Collection**.

  <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/execution-settings/KS-Project-Settings-Email-Test-Suite-Collection-Body-Template.png" width="" alt="Test Suite Collection Report email template">

All fields in the templates are editable. Click **Apply** when finished.

**Where:**

> `executionProfile` is not available in the **Test Suite Collection Execution** email reports.

* hostName: Host's name
* os: Operating system
* suiteCollectionName: Name of Test Suite Collection
* startTime: When the Test Suite Collection started running
* duration: The duration of test execution
* totalPassed: Total passed test cases
* totalFailed: Total failed test cases
* totalError: Total error test cases

## Support Global Variables in Email Settings

From version 7.7.0 onwards, you can customize Email Settings with Global Variables and override their default values via the Command line.

The below section guides you on how to do that with a usage example.

> **Scope of application**:
>
> * When sending email reports on a Test Suite, the Global Variables in the selected Execution Profile are applied.
> * When sending email reports on a Test Suite Collection:
>   * For the Test Suite Collection: only the Global Variables in the Default Profile are applied.
>   * For Test Suites contained in that Test Suite Collection: the Global Variables in the selected Execution Profile of each Test Suite are applied.

1. [Define a Global Variable](https://docs.katalon.com/katalon-studio/docs/execution-profile-v54.html#define-a-global-variable) in your Execution Profile.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/emails-settings/global-variable.png" width=668>

2. Call the [parameterized Global Variable](https://docs.katalon.com/katalon-studio/docs/execution-profile-v54.html#parameterize-a-global-variable) in supported locations including Sender, Recipients, Cc, Bcc, and Subject by using the syntax `${GlobalVariable.name}`. 

    From version 8.3.0 onwards, Katalon Studio supports using global variables in Body Template.
  
    For example, the declared value, "Regression Test - Latest Release", is prepended to the email subject:

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/emails-settings/subject.png" width=578>
   
   Send a test email so you can see the effect.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/emails-settings/email.png" width=915>

When running your Test Suite/Test Suite Collection in console mode, you can also pass another value to override the default value of that Global Variable with the `-g_<variableName>=<variableValue>` syntax. For instance, `-g_<subject>=<Release 7.7>`.
