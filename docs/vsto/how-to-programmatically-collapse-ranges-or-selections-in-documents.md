---
title: "How to: Programmatically Collapse Ranges or Selections in Documents | Microsoft Docs"
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
  - "selections, collapsing"
  - "documents [Office development in Visual Studio], collapsing ranges"
  - "collapsing selections"
  - "ranges, collapsing"
  - "collapsing ranges"
ms.assetid: 0bd059dd-8606-42ae-a8a9-97f8f3bd5cc5
caps.latest.revision: 42
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# How to: Programmatically Collapse Ranges or Selections in Documents
  If you are working with a <xref:Microsoft.Office.Interop.Word.Range> or <xref:Microsoft.Office.Interop.Word.Selection> object, you might want to change the selection to an insertion point before inserting text, to avoid overwriting existing text. Both the <xref:Microsoft.Office.Interop.Word.Range> and <xref:Microsoft.Office.Interop.Word.Selection> objects have a Collapse method, which makes use of the <xref:Microsoft.Office.Interop.Word.WdCollapseDirection> enumeration values:  
  
-   <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> collapses the selection to the beginning of the selection. This is the default if you do not specify an enumeration value.  
  
-   <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> collapses the selection to the end of the selection.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### To collapse a range and insert new text  
  
1.  Create a <xref:Microsoft.Office.Interop.Word.Range> object that consists of the first paragraph in the document.  
  
     The following code example can be used in a document-level customization.  
  
     [!code-vb[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#46)]
     [!code-csharp[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#46)]  
  
     The following code example can be used in an VSTO Add-in. This code uses the active document.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#46)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#46)]  
  
2.  Use the <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> enumeration value to collapse the range.  
  
     [!code-vb[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#47)]
     [!code-csharp[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#47)]  
  
3.  Insert the new text.  
  
     [!code-vb[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#48)]
     [!code-csharp[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#48)]  
  
4.  Select the <xref:Microsoft.Office.Interop.Word.Range>.  
  
     [!code-vb[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#49)]
     [!code-csharp[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#49)]  
  
 If you use the <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> enumeration value, the text is inserted at the beginning of the following paragraph.  
  
 [!code-vb[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#50)]
 [!code-csharp[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#50)]  
  
 You might expect that inserting a new sentence would insert it before the paragraph marker, but that is not the case because the original range includes the paragraph marker. For more information, see [How to: Programmatically Exclude Paragraph Marks When Creating Ranges](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md).  
  
## Document-Level Customization Example  
  
#### To collapse a range in a document-level customization  
  
1.  The following example shows the complete method for a document-level customization. To use this code, run it from the `ThisDocument` class in your project.  
  
     [!code-vb[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#45)]  
  
## VSTO Add-in Example  
  
#### To collapse a range in an VSTO Add-in  
  
1.  The following example shows the complete method for an VSTO Add-in. To use this code, run it from the `ThisAddIn` class in your project.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#45)]  
  
## See Also  
 [How to: Programmatically Insert Text into Word Documents](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [How to: Programmatically Define and Select Ranges in Documents](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [How to: Programmatically Retrieve Start and End Characters in Ranges](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [How to: Programmatically Exclude Paragraph Marks When Creating Ranges](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [How to: Programmatically Extend Ranges in Documents](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [How to: Programmatically Reset Ranges in Word Documents](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)  
  