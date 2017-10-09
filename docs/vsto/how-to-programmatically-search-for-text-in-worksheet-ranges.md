---
title: "How to: Programmatically Search for Text in Worksheet Ranges | Microsoft Docs"
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
  - "worksheets, searching"
  - "text [Office development in Visual Studio], searching in worksheets"
  - "text searches, worksheets"
ms.assetid: a6902711-fefb-450a-a76b-b1446d11c423
caps.latest.revision: 48
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# How to: Programmatically Search for Text in Worksheet Ranges
  The <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> method of the <xref:Microsoft.Office.Interop.Excel.Range> object enables you to search for text within the range. This text can also be any of the error strings that can appear in a worksheet cell such as `#NULL!` or `#VALUE!`. For more information about error strings, see [Cell Error Values](http://msdn.microsoft.com/library/office/ff839168.aspx).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 The following example searches a range named `Fruits` and modifies the font for cells that contain the word "apples". This procedure also uses the <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> method, which uses the previously set search settings to repeat the search. You specify the cell after which to search, and the <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> method handles the rest.  
  
> [!NOTE]  
>  The <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> method's search wraps back to the beginning of the search range after it has reached the end of the range. Your code must ensure that the search does not wrap around in an infinite loop. The sample procedure shows one way to handle this using the <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> property.  
  
 ![link to video](../vsto/media/playvideo.gif "link to video") For a related video demonstration, see [How Do I: Use the Find Method in an Excel Add-in?](http://go.microsoft.com/fwlink/?LinkID=130294).  
  
### To search for text in a worksheet range  
  
1.  Declare variables for tracking the entire range, the first found range, and the current found range.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
     [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]  
  
2.  Search for the first match, specifying all the parameters except the cell to search after.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
     [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]  
  
3.  Continue searching as long as there are matches.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
     [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]  
  
4.  Compare the first found range (`firstFind`) to **Nothing**. If `firstFind` contains no value, the code stores away the found range (`currentFind`).  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
     [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]  
  
5.  Exit the loop if the address of the found range matches the address of the first found range.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
     [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]  
  
6.  Set the appearance of the found range.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
     [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]  
  
7.  Perform another search.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
     [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]  
  
 The following example shows the complete method.  
  
## Example  
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]  
  
## See Also  
 [Working with Ranges](../vsto/working-with-ranges.md)   
 [How to: Programmatically Apply Styles to Ranges in Workbooks](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [How to: Programmatically Refer to Worksheet Ranges in Code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Optional Parameters in Office Solutions](../vsto/optional-parameters-in-office-solutions.md)  
  
  