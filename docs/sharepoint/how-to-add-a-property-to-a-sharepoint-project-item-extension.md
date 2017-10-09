---
title: "How to: Add a Property to a SharePoint Project Item Extension | Microsoft Docs"
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
ms.assetid: 4fd97ef2-86e7-4d92-8e34-5b0ec3cc43a0
caps.latest.revision: 20
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# How to: Add a Property to a SharePoint Project Item Extension
  You can use a project item extension to add a property to any SharePoint project item that is already installed in Visual Studio. The property appears in the **Properties** window when the project item is selected in **Solution Explorer**.  
  
 The following steps assume that you have already created a project item extension. For more information, see [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
### To add a property to a project item extension  
  
1.  Define a class with a public property that represents the property you are adding to a project item type. If you want to add multiple properties to a project item type, you can define all the properties in the same class or in different classes.  
  
2.  In the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> method of your <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implementation, handle the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> event of the *projectItemType* parameter.  
  
3.  In the event handler for the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> event, add an instance of your properties class to the <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> collection of the event arguments parameter.  
  
## Example  
 The following code example demonstrates how to add a property named **Example Property** to the Event Receiver project item.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb#8)]  
  
### Understanding the Code  
 To ensure that the same instance of the `CustomProperties` class is used each time the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> event occurs, the code example adds the properties object to the <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> property of the project item the first time this event occurs. The code retrieves this object whenever this event occurs again. For more information about using the <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> property to associate data with project items, see [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 To persist changes to the property value, the **set** accessor for `ExampleProperty` saves the new value to the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> property of the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> object that the property is associated with. For more information about using the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> property to persist data with project items, see [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### Specifying the Behavior of Custom Properties  
 You can define how a custom property appears and behaves in the **Properties** window by applying attributes from the <xref:System.ComponentModel> namespace to the property definition. The following attributes are useful in many scenarios:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Specifies the name of the property that appears in the **Properties** window.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Specifies the description string that appears in the bottom of the **Properties** window when the property is selected.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Specifies the default value of the property.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Specifies a custom conversion between the string that is displayed in the **Properties** window and a non-string property value.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Specifies a custom editor to use to modify the property.  
  
## Compiling the Code  
 These examples require a class library project with references to the following assemblies:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Deploying the Extension  
 To deploy the extension, create a [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) package for the assembly and any other files that you want to distribute with the extension. For more information, see [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## See Also  
 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  