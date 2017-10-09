---
title: "How to: Programmatically Extend Ranges in Documents | Microsoft Docs"
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
  - "ranges, extending"
  - "documents [Office development in Visual Studio], extending ranges"
ms.assetid: 055af7a4-13d5-4236-b5fb-a112721482c5
caps.latest.revision: 41
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# How to: Programmatically Extend Ranges in Documents
  After you define a <xref:Microsoft.Office.Interop.Word.Range> object in a Microsoft Office Word document, you change its start and end points by using the <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> and <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> methods. The <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> and <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> methods take the same two arguments, *Unit* and *Count*. The *Count* argument is the number of units to move, and the *Unit* argument can be one of the following <xref:Microsoft.Office.Interop.Word.WdUnits> values:  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdCharacter>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdWord>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdSentence>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdParagraph>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdSection>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdStory>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdCell>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdColumn>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdRow>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdTable>  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 The following example defines a seven-character range. It then moves the start position of the range seven characters after the original start position. Because the end position of the range was also seven characters after the start position, the result is a range that consists of zero characters. The code then moves the end position seven characters after the current end position.  
  
### To extend a range  
  
1.  Define a range of characters. For more information, see [How to: Programmatically Define and Select Ranges in Documents](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).  
  
     The following code example can be used in a document-level customization.  
  
     [!code-vb[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#39)]  
  
     The following code example can be used in an VSTO Add-in. This example uses the active document.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#39)]  
  
2.  Use the <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> method of the <xref:Microsoft.Office.Interop.Word.Range> object to move the start position of the range.  
  
     [!code-vb[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#40)]
     [!code-csharp[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#40)]  
  
3.  Use the <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> method of the <xref:Microsoft.Office.Interop.Word.Range> object to move the end position of the range.  
  
     [!code-vb[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#41)]
     [!code-csharp[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#41)]  
  
## Document-Level Customization Code  
  
#### To extend a range in a document-level customization  
  
1.  The following example shows the complete code for a document-level customization. To use this code, run it from the `ThisDocument` class in your project.  
  
     [!code-vb[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#38)]  
  
## VSTO Add-in Code  
  
#### To extend a range in an application-level VSTO Add-in  
  
1.  The following example shows the complete code for an VSTO Add-in. To use this code, run it from the `ThisAddIn` class in your project.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#38)]  
  
## See Also  
 [How to: Programmatically Reset Ranges in Word Documents](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [How to: Programmatically Collapse Ranges or Selections in Documents](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [How to: Programmatically Define and Select Ranges in Documents](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [How to: Programmatically Retrieve Start and End Characters in Ranges](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [How to: Programmatically Exclude Paragraph Marks When Creating Ranges](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)  
  