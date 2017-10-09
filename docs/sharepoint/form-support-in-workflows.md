---
title: "Form Support in Workflows | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, workflows"
  - "workflows [SharePoint development in Visual Studio]"
ms.assetid: 1706f6a2-ea84-4234-85ae-19feb8540507
caps.latest.revision: 12
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# Form Support in Workflows
  Four types of forms can be used in a workflow: association, initiation, task, and modification. These form types can be based on either an ASPX form or an InfoPath form. The level of support that [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] provides for a particular form depends on several factors, which are described in the following tables. For more information about workflow form types, see [Workflow Forms Overview](http://go.microsoft.com/fwlink/?LinkId=185228) on the MSDN Web site.  
  
## XML Refactoring  
 When you add an ASPX association or initiation form to a [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] workflow project item, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] automatically refactors the XML in the workflow's Elements.xml file to keep the attribute that refers to the association or initiation form in sync whenever the form name or deployment path is updated or the form is deleted. However, when you use other form types in a workflow, such as a task or modification form, the Elements.xml file is not refactored.  
  
## Form Support in New Visual Studio Workflows  
 The following table lists [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] support for different form types on either ASPX or InfoPath forms in workflows that are created in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Form Type|Workflow created in Visual Studio with an ASPX Form|Workflow created in Visual Studio by using an InfoPath Form|  
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|  
|Association|-   An ASPX association form can be added to the workflow by using the **Workflow Association Form** item template.<br />-   The Elements.xml file of the workflow is refactored when the form is added, renamed, or deleted, or when its deployment path changes.<br />-   For more information, see [Walkthrough: Creating a Workflow with Association and Initiation Forms](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-   There is no InfoPath association form template in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-   There is no integration between [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] and InfoPath Designer.<br />-   The Elements.xml file of the workflow is not refactored.|  
|Initiation|-   An ASPX initiation form can be added to the workflow by using the **Workflow Initiation Form** item template.<br />-   The Elements.xml file of the workflow is refactored when the form is added, renamed, or deleted, or when its deployment path changes.<br />-   For more information, see [Walkthrough: Creating a Workflow with Association and Initiation Forms](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).|-   There is no InfoPath association form template in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-   There is no integration between [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] and InfoPath Designer.<br />-   The Elements.xml file of the workflow is not refactored.|  
|Task|-   No ASPX task form template is available in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. You must create an application page and add code to it.<br />-   The Elements.xml file of the workflow is not refactored.<br />-   For more information, see [Workflow Task Forms (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187674)|-   There is no InfoPath task form template in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-   There is no integration between [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] and InfoPath Designer.<br />-   The Elements.xml file of the workflow is not refactored.|  
|Modification|-   No ASPX modification form template is available in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. To add a modification form, you must create an application page and add code to it.<br />-   The Elements.xml file of the workflow is not refactored. You must manually edit it as appropriate.<br />-   For more information, see [Workflow Modification Forms (SharePoint Foundation)](http://go.microsoft.com/fwlink/?LinkId=187675)|-   There is no InfoPath modification form template in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].<br />-   There is no integration between [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] and InfoPath Designer.<br />-   The Elements.xml file of the workflow is not refactored.|  
  
## Form Support in Imported SharePoint Reusable Workflows  
 The following table lists [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] support for different form types on either ASPX or InfoPath forms in SharePoint reusable workflows that are imported into [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
|Form Type|Reusable workflow that has an ASPX form imported from SharePoint Designer|Reusable workflow that has an InfoPath form imported from SharePoint Designer|  
|---------------|-------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|Association|-   The form is referenced in the Elements.xml file of the workflow.<br />-   The Elements.xml file of the workflow is refactored when the form is renamed or deleted, or when its deployment path changes.|-   The form is imported, but not referenced in the Elements.xml of the workflow.<br />-   The Elements.xml file of the workflow is not refactored.|  
|Initiation|-   The form is referenced by the workflow in the Elements.xml file of the workflow.<br />-   The Elements.xml file of the workflow is refactored when the form is renamed or deleted, or when its deployment path changes.|-   The form is imported, but not referenced in the Elements.xml of the workflow.<br />-   The Elements.xml file of the workflow is not refactored. **Note:**  Rules and properties must be added and changed for this scenario to work.|  
|Task|-   The form is referenced in the Elements.xml file of the workflow.<br />-   The Elements.xml file of the workflow is not refactored.|-   The form is imported, but not referenced in the Elements.xml of the workflow.<br />-   The Elements.xml file of the workflow is not refactored. **Note:**  Rules and properties must be added and changed for this scenario to work.|  
|Modification|Not applicable. ASPX modification forms cannot be created in SharePoint Designer.|Not applicable. InfoPath modification forms cannot be created in SharePoint Designer, except for the built-in SharePoint Server workflow, which is not included in the .wsp file when the workflow is exported.|  
  
## See Also  
 [Walkthrough: Creating a Workflow with Association and Initiation Forms](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [Creating SharePoint Workflow Solutions](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Importing Items from an Existing SharePoint Site](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)  
  
  