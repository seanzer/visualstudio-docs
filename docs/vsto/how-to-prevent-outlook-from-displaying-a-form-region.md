---
title: "How to: Prevent Outlook from Displaying a Form Region | Microsoft Docs"
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
  - "form regions [Office development in Visual Studio], canceling display"
  - "canceling form region display"
ms.assetid: 82a25def-776a-476a-a72d-d0a48a827d3c
caps.latest.revision: 24
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# How to: Prevent Outlook from Displaying a Form Region
  There might be situations in which you do not want Microsoft Office Outlook to display a form region for a particular item. For example, if a contact item does not contain a business address, you can prevent a form region that shows the location of the business in a map from appearing.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
### To prevent Outlook from displaying a form region  
  
1.  Open the code file for the form region you want to modify.  
  
2.  Expand the **Form Region Factory** code region.  
  
3.  Add code to the `FormRegionInitializing` event handler that sets the <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> property of the <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> class to **true**.  
  
 In this example, if the contact item does not contain an address, the <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> property is set to **true**, and the form region does not appear.  
  
## Example  
 [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]  
  
## See Also  
 [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md)   
 [Walkthrough: Designing an Outlook Form Region](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [How to: Add a Form Region to an Outlook Add-in Project](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Walkthrough: Designing an Outlook Form Region](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Walkthrough: Importing a Form Region That Is Designed in Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  