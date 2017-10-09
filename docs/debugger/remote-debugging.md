---
title: "Remote debugging in Visual Studio | Microsoft Docs"
ms.custom: "remotedebugging"
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "hero-article"
f1_keywords: 
  - "vs.debug.remote.overview"
dev_langs: 
  - "C++"
  - "FSharp"
  - "CSharp"
  - "JScript"
  - "VB"
helpviewer_keywords: 
  - "remote debugging, setup"
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
caps.latest.revision: 65
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
translation.priority.ht: 
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "ru-ru"
  - "zh-cn"
  - "zh-tw"
translation.priority.mt: 
  - "cs-cz"
  - "pl-pl"
  - "pt-br"
  - "tr-tr"
---
# Remote Debugging
You can debug a Visual Studio application that has been deployed on a different computer. To do so, you use the Visual Studio remote debugger.

For in-depth instructions on remote debugging, see these topics.

|Scenario|Link|
|-|-|-|
|ASP.NET|[Remote Debugging ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) or [Remote Debugging ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|C# or Visual Basic|[Remote Debugging a C# or Visual Basic Project](remote-debugging-csharp.md)|
|C++|[Remote Debugging a C++ Project](remote-debugging-cpp.md)|
|Universal Windows Apps (UWP)|[Debug an Installed App Package](debug-installed-app-package.md)|
|Azure|[Remote Debugging ASP.NET on Azure](remote-debugging-azure.md)|
|Azure Service Fabric|[Debug a remote Service Fabric application](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).|

If you just want to download and install the remote debugger and don't need any additional instructions for your scenario, follow the steps in this article.
  
## Download and Install the Remote Tools  

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="fileshare_msvsmon"></a> (Optional) To run the remote debugger from a file share

You can find the remote debugger (**msvsmon.exe**) on a computer with Visual Studio Community, Professional, or Enterprise already installed. For some scenarios, the easiest way to set up remote debugging is to run the remote debugger (msvsmon.exe) from a file share. For usage limitations, see the remote debugger's Help page (**Help > Usage** in the remote debugger).

1. Find **msvsmon.exe** in the directory matching your version of Visual Studio. For Visual Studio Enterprise 2017:

      **Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe**
      
      **Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\Remote Debugger\x64\msvsmon.exe**

2. Share the **Remote Debugger** folder on the Visual Studio computer.

3. On the remote computer, run **msvsmon.exe**. Follow the [setup instructions](#bkmk_setup).

> [!TIP] 
> For command line installation and command line reference, see the Help page for **msvsmon.exe** by typing ``msvsmon.exe /?`` in the command line on the computer with Visual Studio installed (or go to **Help > Usage** in the remote debugger).
  
## <a name="requirements_msvsmon"></a> Requirements

[!INCLUDE [remote-debugger-requirements](../debugger/includes/remote-debugger-requirements.md)]
  
## Set up the remote debugger  

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

### <a name="configure_msvsmon"></a> Configure the remote debugger  
You can change some aspects of the configuration of the remote debugger after you have started it for the first time.
  
-   If you need to add permissions for other users to connect to the remote debugger, choose **Tools > Permissions**. You must have administrator privileges to grant or deny permissions.

     > [!IMPORTANT] 
     > You can run the remote debugger under a user account that differs from the user account you are using on the Visual Studio computer, but you must add the different user account to the remote debugger's permissions. 

     Alternatively, you can start the remote debugger from the command line with the **/allow \<username>** parameter: **msvsmon /allow \<username@computer>**.
  
-   If you need to change the Authentication mode or the port number, or specify a timeout value for the remote tools: choose **Tools > Options**.  
  
     For a listing of the port numbers used by default, see [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md).  
  
     > [!WARNING]
     >  You can choose to run the remote tools in No Authentication mode, but this mode is strongly discouraged. There is no network security when you run in this mode. Choose the No Authentication mode only if you are sure that the network is not at risk from malicious or hostile traffic.

##  <a name="bkmk_configureService"></a> (Optional) Configure the remote debugger as a service
For debugging in ASP.NET and other server environments, you must either run the remote debugger as an Administrator or, if you want it always running,  run the remote debugger as a service.
  
 If you want to configure the remote debugger as a service, follow these steps.  
  
1.  Find the **Remote Debugger Configuration Wizard** (rdbgwiz.exe). (This is a separate application from the Remote Debugger.) It is available only when you install the remote tools. It is not installed with Visual Studio.  
  
2.  Start running the configuration wizard. When the first page comes up, click **Next**.  
  
3.  Check the **Run the Visual Studio 2015 Remote Debugger as a service** checkbox.  
  
4.  Add the name of the user account and password.  
  
     You may need to add the **Log on as a service** user right to this account (Find **Local Security Policy** (secpol.msc) in the **Start** page or window (or type **secpol** at a command prompt). When the window appears, double-click **User Rights Assignment**, then find **Log on as a service** in the right pane. Double-click it. Add the user account to the **Properties** window and click **OK**). Click **Next**.  
  
5.  Select the type of network that you want the remote tools to communicate with. At least one network type must be selected. If the computers are connected through a domain, you should choose the first item. If the computers are connected through a workgroup or homegroup, you should choose the second or third items. Click **Next**.  
  
6.  If the service can be started, you will see **You have successfully completed the Visual Studio Remote Debugger Configuration Wizard**. If the service cannot be started, you will see **Failed to complete the Visual Studio Remote Debugger Configuration Wizard**. The page also gives some tips to follow to get the service to start.  
  
7.  Click **Finish**.  
  
 At this point the remote debugger is running as a service. You can verify this by going to **Control Panel > Services** and looking for **Visual Studio 2015 Remote Debugger**.  
  
 You can stop and start the remote debugger service from **Control Panel > Services**.

## Set Up Debugging with Remote Symbols 

[!INCLUDE [remote-debugger-symbols](../debugger/includes/remote-debugger-symbols.md)]
  
## See Also  
 [Debugger Feature Tour](../debugger/debugger-feature-tour.md)   
 [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md)   
 [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)   
 [Remote Debugging ASP.NET Core on a Remote IIS Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)  
 [Remote Debugging Errors and Troubleshooting](../debugger/remote-debugging-errors-and-troubleshooting.md)
