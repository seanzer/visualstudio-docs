---
title: "How to: Add and Remove Features and Items to a Package by Using the Packaging Explorer | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.RAD.PackagingExplorer"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint development in Visual Studio, packages"
ms.assetid: 549d5848-f0c9-42c6-b7f5-bc1e626a30e6
caps.latest.revision: 18
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# How to: Add and Remove Features and Items to a Package by Using the Packaging Explorer
  To configure a package to deploy SharePoint items and Features, you can use the Packaging Explorer. You can adjust the SharePoint project items and Features inside your .wsp file.  
  
 Alternatively, you can use the Packaging Designer to view and re-order the Features to change the activation order. For more information, see [How to: Add and Remove Features and Items to a Package by Using the Package Designer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
## Opening the Packaging Explorer  
 You can use the following procedure to open the Packaging Explorer, if your Visual Studio solution has at least one SharePoint project. Alternatively, the Packaging Explorer opens automatically when you view a Feature or package designer. After you close all Feature and package designers, the Packaging Explorer also closes.  
  
#### To open the Packaging Explorer  
  
1.  On the menu bar, choose **View**, **Other Windows**, **Packaging Explorer**.  
  
     The **Packaging Explorer** appears in the **Toolbox**.  
  
## Adding a Feature to a Package  
 You can add new and existing Features to a Package by using the Packaging Explorer.  
  
#### To add a SharePoint Feature  
  
1.  Open the **Packaging Explorer**, open the shortcut menu for the project, and then choose **Add Feature**.  
  
#### To move an existing SharePoint Feature  
  
1.  Open the **Packaging Explorer**, and then perform one of the following steps:  
  
    -   Drag a **Feature** from one project to another project.  
  
    -   Open the shortcut menu for a Feature, choose **Cut**, open the shortcut menu for the project to which you want to move the Feature, and then choose **Paste**.  
  
    > [!NOTE]  
    >  Use this procedure if you have more than one SharePoint project in your solution.  
  
## Validating a Feature or Package  
 You can identify potential problems in the SharePoint Features and packages by validating the files. Warnings and errors are displayed in the Output window and Error List window.  
  
#### To validate a SharePoint Feature or package  
  
1.  Open the **Packaging Explorer**.  
  
2.  Open a shortcut menu for a Feature or package, and then choose **Validate**.  
  
## See Also  
 [Packaging and Deploying SharePoint Solutions](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  