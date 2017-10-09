---
title: "How to: Cache Data in a Password-Protected Document | Microsoft Docs"
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
  - "data caching [Office development in Visual Studio], protected documents"
  - "datasets [Office development in Visual Studio], caching"
  - "data [Office development in Visual Studio], caching"
ms.assetid: 91b865fc-bd01-438f-ac63-2fe3175bc2e8
caps.latest.revision: 23
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# How to: Cache Data in a Password-Protected Document
  If you add data to the data cache in a document or workbook that is protected with a password, changes to the cached data are not saved automatically. You can save changes to the cached data by overriding two methods in your project.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Caching in Word Documents  
  
#### To cache data in a Word document that is protected with a password  
  
1.  In the `ThisDocument` class, mark a public field or property to be cached. For more information, see [Caching Data](../vsto/caching-data.md).  
  
2.  Override the <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> method in the `ThisDocument` class and remove protection from the document.  
  
     When the document is saved, the [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] calls this method to give you an opportunity to unprotect the document. This enables changes to the cached data to be saved.  
  
3.  Override the <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> method in the `ThisDocument` class and reapply protection to the document.  
  
     After the document is saved, the [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] calls this method to give you an opportunity to reapply protection to the document.  
  
### Example  
 The following code example demonstrates how to cache data in a Word document that is protected with a password. Before the code removes the protection in the <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> method, it saves the current <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> value, so that the same type of protection can be reapplied in the <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> method.  
  
 [!code-csharp[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb#1)]  
  
### Compiling the Code  
 Add this code to the `ThisDocument` class in your project. This code assumes that the password is stored in a field named `securelyStoredPassword`.  
  
## Caching in Excel Workbooks  
 In Excel projects, this procedure is necessary only when you protect the entire workbook with a password by using the <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> method. This procedure is not necessary if you protect only a specific worksheet with a password by using the <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> method.  
  
#### To cache data in an Excel workbook that is protected with a password  
  
1.  In the `ThisWorkbook` class or one of the `Sheet`*n* classes, mark a public field or property to be cached. For more information, see [Caching Data](../vsto/caching-data.md).  
  
2.  Override the <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> method in the `ThisWorkbook` class and remove protection from the workbook.  
  
     When the workbook is saved, the [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] calls this method to give you an opportunity to unprotect the workbook. This enables changes to the cached data to be saved.  
  
3.  Override the <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> method in the `ThisWorkbook` class and reapply protection to the document.  
  
     After the workbook is saved, the [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] calls this method to give you an opportunity to reapply protection to the workbook.  
  
### Example  
 The following code example demonstrates how to cache data in an Excel workbook that is protected with a password. Before the code removes the protection in the <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> method, it saves the current <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> and <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> values, so that the same type of protection can be reapplied in the <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> method.  
  
 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs#1)]  
  
### Compiling the Code  
 Add this code to the `ThisWorkbook` class in your project. This code assumes that the password is stored in a field named `securelyStoredPassword`.  
  
## See Also  
 [Caching Data](../vsto/caching-data.md)   
 [How to: Cache Data for Use Offline or on a Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [How to: Programmatically Cache a Data Source in an Office Document](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)  
  
  