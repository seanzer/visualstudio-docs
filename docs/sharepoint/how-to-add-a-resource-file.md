---
title: "How to: Add a Resource File | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "resource files [SharePoint development in Visual Studio]"
  - "SharePoint development in Visual Studio, resource files"
ms.assetid: 2b4ac232-992e-4070-8e98-6f11eb88e1a8
caps.latest.revision: 16
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# How to: Add a Resource File
  The commands for adding resource files is on the shortcut menu of the solution node and feature nodes in Solution Explorer. For more information, see [Localizing SharePoint Solutions](../sharepoint/localizing-sharepoint-solutions.md).  
  
### To add a global resource file to a SharePoint solution  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], open a SharePoint solution.  
  
2.  In **Solution Explorer**, choose a SharePoint project node, and then, on the menu bar, choose **Project**, **Add New Item**.  
  
3.  In the **Add New Item** dialog box, choose the **Global Resources File** template, and then choose the **Add** button.  
  
    > [!NOTE]  
    >  The Global Resources File project item template appears only when a SharePoint project item is selected.  
  
4.  In the **Add Resource** dialog box, choose a culture for the resource file, such as English (United States).  
  
     This step adds a global resource file to your solution in the format, Resource*x***.***culture***.**resx, such as, Resource1.en-US.resx.  
  
5.  When the **Resource Editor** opens in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], add resources to the resource file.  
  
### To add a feature resource file to a SharePoint feature  
  
1.  If the SharePoint solution is not already open in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], open the solution.  
  
2.  In **Solution Explorer**, open the shortcut menu for the name of a feature under the **Features** node, and then choose **Add Feature Resource**.  
  
     This step adds a resource file to the feature in the format, *ResourceFileName***.***culture***.**resx, such as, Feature1.en-US.resx.  
  
3.  When the **Resource Editor** opens in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], add resources to the resource file.  
  
## See Also  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  