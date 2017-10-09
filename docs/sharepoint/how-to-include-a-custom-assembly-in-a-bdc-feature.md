---
title: "How to: Include a Custom Assembly in a BDC Feature | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.BDC.Add_Assemblies_Dialog"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Business Data Connectivity service [SharePoint development in Visual Studio], add reference"
  - "Business Data Connectivity service [SharePoint development in Visual Studio], custom assembly"
  - "BDC [SharePoint development in Visual Studio], custom assembly"
  - "BDC [SharePoint development in Visual Studio], add reference"
ms.assetid: 2ddf44b9-5f51-4bca-b8bb-94c4bbd1c5f3
caps.latest.revision: 17
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# How to: Include a Custom Assembly in a BDC Feature
  Your project can reference assemblies from other projects in the same solution. However, you must add these assemblies to the feature file of the project by using the **Assign referenced assemblies to LobSystems** dialog box.  
  
### To include a custom assembly in a Business Data Connectivity (BDC) feature  
  
1.  In **Solution Explorer**, choose the folder that contains the BDC model.  
  
2.  On the **View** menu, click **Properties Window**.  
  
3.  In the **Properties** window, choose the **Assemblies** property, and then the ellipsis button (![ASP.NET Mobile Designer ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile Designer ellipse")).  
  
     The **Assign referenced assemblies to LobSystems** dialog box appears.  
  
4.  In the **Select an Assembly** list, choose the custom assembly.  
  
    > [!NOTE]  
    >  Assemblies only appear in the **Assign referenced assemblies to LobSystems** dialog box if you have added a reference to the project that contains the assembly. For more information, see [How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
5.  In the **Reference Properties** group, open the list that appears for the **LobSystem Scope** property, choose the LOB System of the methods that use the custom assembly, and then choose the **OK** button.  
  
    > [!NOTE]  
    >  To debug code in the custom assembly, you must add the assembly to the solution package. For more information, see [How to: Add and Remove Additional Assemblies](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
## See Also  
 [How to: Use a Resource File to Specify Localized Names, Properties, and Permissions](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [How to: Add an Existing BDC Model File to a SharePoint Project](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Creating a Business Data Connectivity Model](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [How to: Create a BDC Model](../sharepoint/how-to-create-a-bdc-model.md)   
 [Integrating Business Data into SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  