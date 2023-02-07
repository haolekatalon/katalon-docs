---
title: "Set up WinAppDriver" 
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/setup-winappdriver.html 
---
This document shows you how to install and run Windows Application Driver (WinAppDriver) on a Windows 10 machine before performing Windows Desktop Apps tests. 

> What is the test machine?
>
> The test machine is where you have the Application Under Test installed and tested.

> What is the test runner machine?
> 
> * The test runner machine is where you install Katalon Studio and store the test scripts. 
> * The test runner machine and the test machine can be the same machine or different ones (remote connection).
## Install & Run WinAppDriver on Windows 10 machine
### Install WinAppDriver

> Notes:
> 
> Install and run WinAppDriver on the test machine. 

There are two ways to install WinAppDriver on a Windows 10 machine:

1. From the Katalon Studio toolbar, select **Tools > Windows > Install WinAppDrivers**. The **Windows Application Driver Setup** window opens. Follow the instructions to install the Windows Application Driver.

2. You can also refer to the WinAppDriver Github project document here: [Installing and Running Windows Application Driver](https://github.com/microsoft/WinAppDriver#installing-and-running-windows-application-driver) for the installation. 
### Run WinAppDriver

1. Enable **Developer Mode** on the test machine. You can refer to the Microsoft document here: [Enable your device for development](https://docs.microsoft.com/en-us/windows/uwp/get-started/enable-your-device-for-development) for instructions.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/introduction-desktop-app-testing/dev-mode.png" width="305.5" height="">
   
2. By default, WinAppDriver is installed at `C:\Program Files (x86)\Windows Application Driver`. To run WinAppDriver, double-click the `WinAppDriver.exe` file from the installation directory. 

## Set up WinAppDriver for the remote connection
### On the Windows 10 test machine

> Notes:
> 
> * While the test is being run, make sure to have WinAppDriver open and configured for the remote connection on the Windows 10 test machine.

After installing WinAppDriver and enabling **Developer Mode**, to configure WinAppDriver for the remote connection, follow these steps:

1. Open **Task Manager** > Select **File** > Create a new task.
2. Select **Create this task with administrative privileges** and enter `cmd` in the **Open** text box, then click the **OK** button.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/introduction-desktop-app-testing/Set-up-1.png" width="476" height="171">

3. Run `cd` to your WinAppDriver installation folder. By default, it is at `C:\Program Files (x86)\Windows Application Driver`.
4. Run `WinAppDriver.exe <IP_Adress> <Port>`.
    
    * `IP_Adress`: is the public IP address of the test machine. Run `ipconfig.exe` to determine the IP address.
    * `Port`: is the public port of the remote machine. By default, it should be 4723.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/introduction-desktop-app-testing/Set-up-2.png" width="690" height="146">

   > Notes: 
   > 
   > If the test machine is in a highly secured environment with firewall, you might need to create an Inboud Port Rule for the test machine to receive inbound requests. To set up the inbound rule, you can follow the steps here in the WinAppDriver project document: [Create an Inbound Port Rule](https://github.com/microsoft/WinAppDriver/blob/master/Docs/RunningOnRemoteMachine.md).
### On the test runner machine

> Notes:
> 
> * The test runner machine can be Windows, macOS or Linux.

While building your test script, make sure to have the `WinAppDriver URL` point to the public IP address of the remote test machine. In the above example, it should be: `http://192.168.37.95:4723/`.

The application file path is the absolute path to the `Windows Executable File (*.exe)` file of the remote test machine.

   <img src="https://github.com/katalon-studio/docs-images/raw/3672749302fd26a6ee095ed5217b2be05aaf6d78/katalon-studio/docs/introduction-desktop-app-testing/KS-Windows-Remote-connection-3.png" width="90%" alt="Remote connection in Katalon">

**Next step:**

After setting up WinAppDriver, you can begin creating your first Windows Desktop Apps tests. You can refer to the following document for further details: 
* [Create test cases using Windows Record Utility](https://docs.katalon.com/katalon-studio/docs/windows-recorder-tutorials.html#coordinate-based-recording)
* [Create test cases using Windows Spy Utility](https://docs.katalon.com/katalon-studio/docs/windows-spy-tutorials.html)