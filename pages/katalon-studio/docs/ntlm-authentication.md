---
title: "NTLM Authentication" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/ntlm-authentication.html 
redirect_from:
description: 
---

From version 8.4.0 beta, Katalon Studio supports NTLM authentication.

## Requirements

* An active Katalon Studio Enterprise license.
* Katalon Studio version 8.4.0 beta onwards. Download from our GitHub repository: [Katalon Studio version 8.4.0 beta](https://github.com/katalon-studio/katalon-studio/releases/tag/v8.4.0.beta).
* Connection to a server that has NTLM Windows Authentication enabled. To check your connection to the server, open the terminal/command line and type: `ping <ip_address>`.

> Notes:
>
> The NTLM authentication in Katalon Studio is tested with:
>
> * Windows Server 2003 systems, configured to use LM and NTLMv1 authentication.
> * Windows Server 2016 systems, configured to use NTLM2SessionResponse authentication.

## What is NTLM authentication?

Windows New Technology LAN Manager (NTLM) is an authentication protocol used for Windows authentication with systems configured as members of workgroups. NTLM applies to web application authentication when the organization uses a domain controller for user domain and identity management. A domain controller is a server running a Windows Server operating system version with Active Directory Domain Services installed.

To learn more about domain controllers and NTLM, you can refer to Microsoft documentation: [Domain Controller Roles](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2003/cc786438(v=ws.10)) and [Microsoft NTLM](https://docs.microsoft.com/en-us/windows/win32/secauthn/microsoft-ntlm).

## Use NTLM Authorization in Katalon Studio

1. Open your web service request object.
2. In the web service request object editor, switch to the **Authorization** tab.
3. Choose **Authorization** type as **NTLM**.

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/ntlm/choose-ntlm.png" alt="choose NTLM authorization" width="100%">

4. Input the following information:

    <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/ntlm/ntlm-authentication.png" alt="NTLM authentication" width="100%">

    * **Username**: The username of the account used to authenticate. The username should not include the domain. For example: "user" is correct, whereas "DOMAIN\user" is not.
    * **Password**: The password of the account used to authenticate.
    * **Domain (Optional)**: The domain to authenticate against. If you are using a domain account, you need to input your domain to avoid the error: `401 Unauthorized: Access is denied due to invalid credentials`. If you are using a local account to log in, you can leave this field empty.
    * **Workstation (Optional)**: The hostname of your computer. Naming your workstation helps better management since the workstation name is more straightforward to track than an IP address when logging in to another machine.

5. To update inputs to the request, click **Update**.

NTLM authenticates connections, not requests. Therefore, the NTLM authorization inputs are updated directly to the request, not to the HTTP Header.

Once the log-on is successful, you can see the workstation name and domain information in event 4624.

<img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/ntlm/event-4624.png" alt="event 4624" width="100%">

You can learn more about the 4624 event at Microsoft documentation: [4624(S): An account was successfully logged on](https://docs.microsoft.com/en-us/windows/security/threat-protection/auditing/event-4624).
