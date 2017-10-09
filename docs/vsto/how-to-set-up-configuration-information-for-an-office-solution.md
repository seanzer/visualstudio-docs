---
title: "How to: Set Up Configuration Information for an Office Solution | Microsoft Docs"
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
  - "solutions [Office development in Visual Studio], configuration files"
  - "configuration files [Office development in Visual Studio]"
ms.assetid: f123838f-957a-4cf5-acc0-0cc0f4c2aea2
caps.latest.revision: 33
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# How to: Set Up Configuration Information for an Office Solution
  You can use configuration files to configure settings that are specific to your Office solutions. You can specify settings such as assembly binding policy, remoting objects, debug, and trace settings.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### To add a configuration file to your Office project  
  
1.  On the **Project** menu, click **Add New Item**.  
  
2.  In the **Categories** pane, click **General**.  
  
3.  In the **Templates** pane, select **Application Configuration File**.  
  
4.  In the **Name** box, type the same name as the assembly plus the extension .config. For example, a configuration file for an Excel project assembly called ExcelWorkbook1.dll would be named ExcelWorkbook1.dll.config.  
  
5.  Click **Add**.  
  
6.  Create your configuration file according to the application configuration file schema. For more information, see [Configuration File Schema for the .NET Framework](/dotnet/framework/configure-apps/file-schema/index).  
  
 There are no special considerations for using configuration files with Office projects.  
  
## See Also  
 [Configuration File Schema for the .NET Framework](/dotnet/framework/configure-apps/file-schema/index)   
 [Designing and Creating Office Solutions](../vsto/designing-and-creating-office-solutions.md)   
 [Deploying an Office Solution](../vsto/deploying-an-office-solution.md)  
  
  