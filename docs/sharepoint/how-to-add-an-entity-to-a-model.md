---
title: "How to: Add an Entity to a Model | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EntityTool"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [SharePoint development in Visual Studio], entity"
  - "Business Data Connectivity service [SharePoint development in Visual Studio], adding an entity"
  - "Business Data Connectivity service [SharePoint development in Visual Studio], entity"
  - "BDC [SharePoint development in Visual Studio], adding an entity"
ms.assetid: 139a6639-dabe-4e14-bb64-e5f4efb6f2fb
caps.latest.revision: 23
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# How to: Add an Entity to a Model
  To create an entity, add an entity control from the Visual Studio **Toolbox** onto the Business Data Connectivity (BDC) designer.  
  
### To add an entity to the model  
  
1.  Create a BDC project, or open an existing BDC project. For more information, see [Creating a Business Data Connectivity Model](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
2.  In the **Toolbox**, from the **BusinessDataCatalog** group, add an **Entity** control onto the designer.  
  
     The new entity appears on the designer. Visual Studio adds an `<Entity>` element to the XML of the BDC model file in your project. For more information about the attributes of an Entity element, see [Entity](http://go.microsoft.com/fwlink/?LinkId=169296).  
  
3.  On the designer, open the shortcut menu for the entity, choose **Add**, and then choose **Identifier**.  
  
     A new identifier appears on the entity.  
  
    > [!NOTE]  
    >  You can change the name of the entity and the identifier in the **Properties** window.  
  
4.  Define the fields of the entity in a class. You can either add a new class to the project or use an existing class created by using other tools such as the Object Relational Designer (O/R Designer). The following example shows an entity class named Contact.  
  
     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]  
  
## See Also  
 [How to: Add a Creator Method](../sharepoint/how-to-add-a-creator-method.md)   
 [How to: Add a Deleter Method](../sharepoint/how-to-add-a-deleter-method.md)   
 [How to: Add an Updater Method](../sharepoint/how-to-add-an-updater-method.md)   
 [How to: Add a Finder Method](../sharepoint/how-to-add-a-finder-method.md)   
 [How to: Add a Specific Finder Method](../sharepoint/how-to-add-a-specific-finder-method.md)  
  
  