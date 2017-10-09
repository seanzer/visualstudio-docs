---
title: "Converting Between SharePoint Project System Types and Other Visual Studio Project Types | Microsoft Docs"
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
  - "SharePoint project service"
ms.assetid: ad5d8ab2-1659-4e6a-8783-47e0dad44b11
caps.latest.revision: 13
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# Converting Between SharePoint Project System Types and Other Visual Studio Project Types
  In some cases you might have an object in the SharePoint project system and you want to use features of a corresponding object in the Visual Studio automation object model or integration object model, or vice versa. In these cases, you can use the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> method of the SharePoint project service to convert the object to a different object model.  
  
 For example, you might have an <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> object, but you want to use methods that are only available on an <xref:EnvDTE.Project> or <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> object. In this case, you can use the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> method to convert the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> to an <xref:EnvDTE.Project> or <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>.  
  
 For more information about the Visual Studio automation object model and the Visual Studio integration object model, see [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).  
  
## Types of Conversions  
 The following table lists the types that this method can convert between the SharePoint project system and the other Visual Studio object models.  
  
|SharePoint project system type|Corresponding types in the automation and integration object models|  
|------------------------------------|-------------------------------------------------------------------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> or<br /><br /> Any interface in the Visual Studio integration object model that is implemented by the underlying COM object for the project. These interfaces include <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> (or a derived interface), and <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. For a list of the main interfaces that are implemented by projects, see [Project Model Core Components](/visualstudio/extensibility/internals/project-model-core-components).|  
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> or<br /><br /> A<xref:System.UInt32> value (also called a VSITEMID) that identifies the project member in the <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> that contains it. This value can be passed to the *itemid* parameter of some <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> methods.|  
  
## Example  
 The following code example demonstrates how to use the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> method to convert an <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> object to an <xref:EnvDTE.Project>.  
  
 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb#2)]  
  
 This example requires:  
  
-   An extension of the SharePoint project system that has a reference to the EnvDTE.dll assembly. For more information, see [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   Code that registers the `projectService_ProjectAdded` method to handle the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> event of an <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> object. For an example, see [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## See Also  
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [How to: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
  