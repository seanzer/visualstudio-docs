---
title: "How to: Programmatically Restore Selections After Searches | Microsoft Docs"
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
  - "searches, restoring selection after"
  - "documents [Office development in Visual Studio], restoring selections"
  - "selections, restoring after a search"
ms.assetid: 1e6131ad-0e5b-4189-be67-5b2ed87d193d
caps.latest.revision: 35
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# How to: Programmatically Restore Selections After Searches
  If you find and replace text in a document, you might want to restore the user's original selection after the search is completed.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 The code in the sample procedure makes use of two <xref:Microsoft.Office.Interop.Word.Range> objects. One stores the current <xref:Microsoft.Office.Interop.Word.Selection>, and one sets the entire document to use as a search range.  
  
### To restore the user's original selection after a search  
  
1.  Create the <xref:Microsoft.Office.Interop.Word.Range> objects for the document and the current selection.  
  
     [!code-vb[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#83)]
     [!code-csharp[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#83)]  
  
2.  Perform the search and replace operation.  
  
     [!code-vb[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#84)]
     [!code-csharp[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#84)]  
  
3.  Select the start range to restore the user's original selection.  
  
     [!code-vb[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#85)]
     [!code-csharp[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#85)]  
  
 The following example shows the complete method.  
  
## Example  
 [!code-vb[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#82)]
 [!code-csharp[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#82)]  
  
## See Also  
 [How to: Programmatically Search for and Replace Text  in Documents](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [How to: Programmatically Set Search Options in Word](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [How to: Programmatically Loop Through Found Items in Documents](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Optional Parameters in Office Solutions](../vsto/optional-parameters-in-office-solutions.md)  
  
  