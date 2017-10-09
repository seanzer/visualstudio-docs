---
title: "Troubleshooting Office Solution Security | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "security [Office development in Visual Studio], troubleshooting"
ms.assetid: 6f85dd61-31f5-47da-8409-21ad827eb2dd
caps.latest.revision: 29
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# Troubleshooting Office Solution Security
  This topic contains tips for solving common problems that you might encounter when you work with securing Office solutions.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Trusted Solutions Cannot Be Installed from Restricted Sites  
 Users cannot install a solution from a web location if the web site is listed in the Internet Explorer restricted sites zone. This is true even if the solution is signed with a trusted certificate.  
  
 The URL of the deployment manifest can be categorized into one of five zones:  
  
-   My Computer  
  
-   Internet  
  
-   Local intranet  
  
-   Trusted sites  
  
-   Restricted sites  
  
 If the location of the deployment manifest has been assigned to the restricted sites zone, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] does not install the solution. If the location is known and can be trusted, the user can remove the location from the restricted sites zone and install the solution. For information about how to manage zones, see [Configuring ClickOnce Trusted Publishers](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## Solutions Cannot Be Installed from Network File Shares or Web Locations when Internet Explorer Enhanced Security Configuration or Internet Explorer 7 Is Installed  
 Internet Explorer Enhanced Security Configuration (IEESC) in Windows Server 2003 and higher, and Internet Explorer 7 and higher, significantly restricts the ability of users to browse the Internet. When users try to install Office solutions from a network file share or web location, they might get the following error message: "Customized functionality in this application will not work because the certificate used to sign the deployment manifest for *SolutionName* is not trusted. Contact your administrator for further assistance."  
  
 With IEESC and Internet Explorer 7 and higher, if the URL of the deployment manifest is categorized in the Internet zone, the manifest must have a certificate from a trusted publisher or the solution cannot be installed. Without IEESC, the default behavior is to prompt the end user to make a trust decision.  
  
 To manage the effect of IEESC and Internet Explorer 7 and higher, identify web sites and universal naming convention (UNC) paths that you trust and add them to one of the trusted security zones (Local intranet or Trusted sites).For information about how to manage zones, see [Configuring ClickOnce Trusted Publishers](http://go.microsoft.com/fwlink/?LinkId=94774).  
  
## See Also  
 [Securing Office Solutions](../vsto/securing-office-solutions.md)  
  
  