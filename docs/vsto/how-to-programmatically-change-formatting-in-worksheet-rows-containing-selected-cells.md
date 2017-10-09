---
title: "How to: Programmatically Change Formatting in Worksheet Rows Containing Selected Cells | Microsoft Docs"
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
  - "rows [Office development in Visual Studio]"
  - "formatting [Office development in Visual Studio]"
  - "worksheets, changing formatting"
ms.assetid: c55cd488-98d1-46c6-9715-0e9212d178de
caps.latest.revision: 38
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# How to: Programmatically Change Formatting in Worksheet Rows Containing Selected Cells
  You can change the font of an entire row that contains a selected cell so that the text is bold.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### To make the current row bold and the previously bolded row normal  
  
1.  Declare a static variable to keep track of the previously selected row.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#37](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#37)]
     [!code-vb[Trin_VstcoreExcelAutomation#37](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#37)]  
  
2.  Retrieve a reference to the current cell using the <xref:Microsoft.Office.Interop.Excel._Application.ActiveCell%2A> property.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#38](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#38)]
     [!code-vb[Trin_VstcoreExcelAutomation#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#38)]  
  
3.  Style the current row bold using the <xref:Microsoft.Office.Interop.Excel.Range.EntireRow%2A> property of the active cell.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#39](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#39)]
     [!code-vb[Trin_VstcoreExcelAutomation#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#39)]  
  
4.  Ensure that the current value of `previousRow` is not 0. A 0 (zero) indicates that this is the first time through this code.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#40](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#40)]
     [!code-vb[Trin_VstcoreExcelAutomation#40](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#40)]  
  
5.  Ensure that the current row is different from the previous row.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#41](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#41)]
     [!code-vb[Trin_VstcoreExcelAutomation#41](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#41)]  
  
6.  Retrieve a reference to a range that represents the row that was previously selected, and set that row to not be bold.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#42](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#42)]
     [!code-vb[Trin_VstcoreExcelAutomation#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#42)]  
  
7.  Store the current row so that it can become the previous row on the next pass.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#43](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#43)]
     [!code-vb[Trin_VstcoreExcelAutomation#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#43)]  
  
 The following example shows the complete method.  
  
## Example  
 [!code-csharp[Trin_VstcoreExcelAutomation#36](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#36)]
 [!code-vb[Trin_VstcoreExcelAutomation#36](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#36)]  
  
## See Also  
 [Working with Worksheets](../vsto/working-with-worksheets.md)   
 [How to: Programmatically Apply Styles to Ranges in Workbooks](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [How to: Programmatically Copy Data and Formatting across Worksheets](../vsto/how-to-programmatically-copy-data-and-formatting-across-worksheets.md)   
 [Optional Parameters in Office Solutions](../vsto/optional-parameters-in-office-solutions.md)  
  
  