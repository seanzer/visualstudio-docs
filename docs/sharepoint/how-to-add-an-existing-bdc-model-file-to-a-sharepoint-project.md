---
title: "How to: Add an Existing BDC Model File to a SharePoint Project | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.BDC.ImportDialog"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Business Data Connectivity service [SharePoint development in Visual Studio], import a model"
  - "Business Data Connectivity service [SharePoint development in Visual Studio], reuse a model"
  - "BDC [SharePoint development in Visual Studio], import a model"
  - "BDC [SharePoint development in Visual Studio], remove a model"
ms.assetid: e843738a-f936-4dcd-be35-249407573b74
caps.latest.revision: 16
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# How to: Add an Existing BDC Model File to a SharePoint Project
  You can customize, package, and redeploy a Business Data Connectivity (BDC) model by using Visual Studio to add the model file (.bdcm) to any SharePoint farm project. For more information, see [Creating a Business Data Connectivity Model](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
### To add a BDC model file to a SharePoint project  
  
1.  In **Solution Explorer**, choose the folder for a SharePoint project.  
  
2.  On the menu bar, choose **Project**, **Add Existing Item**.  
  
3.  In the **Add Existing Item** dialog box, browse to the location of the model definition file that you want to add to your project, choose the file, and then choose the **Add** button.  
  
     If the model doesn't define a *Line of Business (LOB) System of type .NET assembly*, the **Add .NET assembly LobSystem** dialog box opens.  
  
4.  If the dialog box appears, perform one of the following steps:  
  
    -   If you want to write custom code and use a designer to define the metadata for the imported model, choose the **Yes** button, name the system, and then choose the **OK** button.  
  
    -   Otherwise, choose the **No** button, and then choose the **OK** button.  
  
     The **Business Data Connectivity Model** item is added to the project.  
  
## See Also  
 [Creating a Business Data Connectivity Model](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [How to: Create a BDC Model](../sharepoint/how-to-create-a-bdc-model.md)   
 [How to: Use a Resource File to Specify Localized Names, Properties, and Permissions](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [How to: Include a Custom Assembly in a BDC Feature](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrating Business Data into SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  