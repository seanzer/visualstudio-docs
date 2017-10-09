---
title: "How to: Programmatically Format Text in Documents | Microsoft Docs"
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
  - "formatting [Office development in Visual Studio]"
  - "documents [Office development in Visual Studio], formatting text"
  - "text [Office development in Visual Studio], formatting in documents"
ms.assetid: 0a84893b-5ccc-4515-a2dc-95773ee8eaba
caps.latest.revision: 42
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# How to: Programmatically Format Text in Documents
  You can use the <xref:Microsoft.Office.Interop.Word.Range> object to format text in a Microsoft Office Word document.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 The following example selects the first paragraph in the document and changes the font size, the font name, and the alignment. It then selects the range and displays a message box to pause before executing the next section of code. The next section calls the Undo method of the <xref:Microsoft.Office.Tools.Word.Document> host item (for a document-level customization) or the <xref:Microsoft.Office.Interop.Word.Document> class (for a VSTO Add-in) three times. It applies the Normal Indent style and displays a message box to pause the code. Then the code calls the <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> method once, and displays a message box.  
  
## Document-Level Customization Example  
  
#### To format text using a document-level customization  
  
1.  The following example can be used in a document-level customization. To use this code, run it from the `ThisDocument` class in your project.  
  
     [!code-vb[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#62)]  
  
## VSTO Add-in Example  
  
#### To format text using a VSTO Add-in  
  
1.  The following example can be used in a VSTO Add-in. This example uses the active document. To use this code, run it from the `ThisAddIn` class in your project.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#62)]  
  
## See Also  
 [How to: Programmatically Define and Select Ranges in Documents](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [How to: Programmatically Insert Text into Word Documents](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [How to: Programmatically Search for and Replace Text  in Documents](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)  
  
  