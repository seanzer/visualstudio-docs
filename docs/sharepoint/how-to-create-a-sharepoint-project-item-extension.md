---
title: "How to: Create a SharePoint Project Item Extension | Microsoft Docs"
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
  - "project items [SharePoint development in Visual Studio], extending"
  - "SharePoint project items, extending"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: 163738b9-e25a-49c9-8f33-4b57a2da6b07
caps.latest.revision: 31
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# How to: Create a SharePoint Project Item Extension
  Create a project item extension when you want to add functionality to a SharePoint project item that is already installed in Visual Studio. For more information, see [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md).  
  
### To create a project item extension  
  
1.  Create a class library project.  
  
2.  Add references to the following assemblies:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Create a class that implements the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interface.  
  
4.  Add the following attributes to the class:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>. This attribute enables Visual Studio to discover and load your <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implementation. Pass the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> type to the attribute constructor.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. In a project item extension, this attribute identifies the project item you want to extend. Pass the ID of the project item to the attribute constructor. For a list of the IDs of the project items that are included with Visual Studio, see [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md).  
  
5.  In your implementation of the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> method, use members of the *projectItemType* parameter to define the behavior of your extension. This parameter is an <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> object that provides access to the events defined in the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> and <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> interfaces. To access a specific instance of the project item type you are extending, handle <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> events such as <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> and <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.  
  
## Example  
 The following code example demonstrates how to create a simple extension for the Event Receiver project item. Each time the user adds an Event Receiver project item to a SharePoint project, this extension writes a message to the **Output** window and **Error List** window.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemextension.vb#1)]  
  
 This example uses the SharePoint project service to write the message to the **Output** window and **Error List** window. For more information, see [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
## Compiling the Code  
 This example requires references to the following assemblies:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Deploying the Extension  
 To deploy the extension, create a [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) package for the assembly and any other files that you want to distribute with the extension. For more information, see [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## See Also  
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  