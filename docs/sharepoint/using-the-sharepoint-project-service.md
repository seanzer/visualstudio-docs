---
title: "Using the SharePoint Project Service | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, extensibility features"
ms.assetid: bfb6cbc7-6c28-4e1a-abb4-88f149e7712c
caps.latest.revision: 34
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# Using the SharePoint Project Service
  The SharePoint project system includes a project service that you can use to perform tasks related to the project system. The project service is an <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> object.  
  
 You can access the SharePoint project service in any SharePoint tools extension. You can also access it in other types of Visual Studio extensions, such as add-ins and VSPackages. For more information, see [How to: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).  
  
## Project Service Features  
 The following table lists the tasks that you can perform by using the SharePoint project service and the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> method or property to use to perform each task.  
  
|Task|Member to use|  
|----------|-------------------|  
|Access any SharePoint project that is open in Visual Studio.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A> property.|  
|Access all of the SharePoint project item types that are available (including built-in and custom project item types).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A> property.|  
|Access all of the deployment steps that are available to SharePoint projects (including built-in and custom deployment steps).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A> property.|  
|Access events that are raised when a developer refactors code in a SharePoint project.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A> property.|  
|Execute a custom *SharePoint command* that calls into the SharePoint server object model. For more information about SharePoint commands, see [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> property.|  
|Convert a type in the SharePoint project system to a type in the Visual Studio automation object model or integration object model, and vice versa. For more information, see [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> method.|  
|Write messages to the **Output** window or **Error List** window in Visual Studio.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A> property.|  
|Access other services that are available in Visual Studio.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A> property.|  
|Retrieve the path to the installation folder of the local SharePoint site that is used for debugging the solution.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A> property.|  
|Determine whether [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] or [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] is installed on the computer.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A> property.|  
|Validate a feature or package in a SharePoint solution.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A> property.|  
  
## See Also  
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [How to: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [How to: Get a Service from the DTE Object](http://msdn.microsoft.com/library/bb166401.aspx)  
  
  