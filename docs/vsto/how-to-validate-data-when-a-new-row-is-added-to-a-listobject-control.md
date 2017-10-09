---
title: "How to: Validate Data When a New Row is Added to a ListObject Control | Microsoft Docs"
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
  - "controls [Office development in Visual Studio], validating data"
  - "ListObject control, new row"
  - "ListObject control, validating data"
ms.assetid: 107bce92-e5ef-40be-8c05-cd6861d39d75
caps.latest.revision: 43
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# How to: Validate Data When a New Row is Added to a ListObject Control
  Users can add new rows to a <xref:Microsoft.Office.Tools.Excel.ListObject> control that is bound to data. You can validate the user's data before committing the changes to the data source.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Data Validation  
 Whenever a row is added to a <xref:Microsoft.Office.Tools.Excel.ListObject> that is bound to data, the <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> event is raised. You can handle this event to perform your data validation. For example, if your application requires that only employees between the ages of 18 and 65 can be added to the data source, you can verify that the age entered falls within that range before the row is added.  
  
> [!NOTE]  
>  You should always check user input on the server in addition to the client. For more information, see [Secure Client Applications](/dotnet/framework/data/adonet/secure-client-applications).  
  
#### To validate data when a new row is added to data-bound ListObject  
  
1.  Create variables for the ID and <xref:System.Data.DataTable> at the class level.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#8)]  
  
2.  Create a new <xref:System.Data.DataTable> and add sample columns and data in the `Startup` event handler of the `Sheet1` class (in a document-level project) or `ThisAddIn` class (in an VSTO Add-in project).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#9)]  
  
3.  Add code to the `list1_BeforeAddDataBoundRow` event handler to check whether the age entered falls within the acceptable range.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#10)]  
  
## Compiling the Code  
 This code example assumes that you have an existing <xref:Microsoft.Office.Tools.Excel.ListObject> named `list1` on the worksheet in which this code appears.  
  
## See Also  
 [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controls on Office Documents](../vsto/controls-on-office-documents.md)   
 [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [ListObject Control](../vsto/listobject-control.md)   
 [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md)   
 [How to: Map ListObject Columns to Data](../vsto/how-to-map-listobject-columns-to-data.md)  
  
  