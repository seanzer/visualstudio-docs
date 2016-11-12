---
title: "One or more projects failed to convert. These projects are now unloaded and marked as unavailable in Solution Explorer. Reload those projects to determine the cause. | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.projectmigrationsfailed"
ms.assetid: c2fd3bbd-15f0-4b30-97f5-59abeae02141
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
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
# One or more projects failed to convert. These projects are now unloaded and marked as unavailable in Solution Explorer. Reload those projects to determine the cause.
You have attempted to open a Solution containing one or more projects that were created in a previous version of Visual Studio. Certain projects could not be converted, and will be marked as (unavailable) in Solution Explorer. These projects must be converted to current formats before your solution can be opened and edited, and the repaired projects can be used in the version of Visual Studio installed on your computer.  
  
### To respond to this message  
  
1.  Select **Yes** to close the dialog box.  
  
     Projects that could not be converted are marked **(unavailable)** in Solution Explorer.  
  
2.  Reload the projects that could not be converted.  
  
    1.  In Solution Explorer, select each project in the active solution that is marked **(unavailable)**.  
  
    2.  On the **Project** menu, choose **Reload Project**.  
  
3.  Review carefully any error messages that display information on problems with projects. Possible problems include:  
  
    1.  Project is read-only. Read-only projects are not converted. These projects can be converted only by users who have permission to edit them.  
  
    2.  Project is already checked out exclusively to another user. That user must check the project back in before you can check it out.  
  
    3.  Project could not be checked out from a network server. Confirm network conditions, and try again.  
  
    4.  Project is corrupted, and must be rebuilt.  
  
4.  Address the problems indicated as you attempt to reload the projects that were marked **(unavailable)**.  
  
5.  Reopen and convert these projects. You might wish to make back-up copies of your project files before converting them.  
  
    > [!NOTE]
    >  As certain project types are converted, for example Visual C++ projects, the former project files are marked with the file extension .old and saved in the project directory.  
  
 If you are part of a development team, everyone who is working on a project should have the same version of Visual Studio installed on their local machines. To ensure that your project remains accessible, communicate regularly with your team.  
  
> [!CAUTION]
>  If the projects in your solution are stored under source code control and you intend to check the converted projects back in, determine first whether other solutions share any of these projects. Do not check in converted projects that are still being used in unconverted solutions. This will break the dependencies within those solutions, and prevent them from opening or building properly.  
  
## See Also  
 [NIB:How to: Unload and Reload Projects](http://msdn.microsoft.com/en-us/abc0155b-8fcb-4ffc-95b6-698518a7100b)   
 [Project Dependencies Dialog Box](http://msdn.microsoft.com/en-us/d66e48c3-3722-40dd-99b4-53d93cac128e)   
 [Compiling and Building](../ide/compiling-and-building-in-visual-studio.md)