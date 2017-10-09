---
title: "How to: Add Custom XML Parts to Document-Level Customizations | Microsoft Docs"
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
  - "document-level customizations [Office development in Visual Studio], custom XML parts"
  - "Office documents [Office development in Visual Studio, custom XML parts"
  - "Word [Office development in Visual Studio], custom XML parts"
  - "Excel [Office development in Visual Studio], custom XML parts"
  - "custom XML parts [Office development in Visual Studio], adding"
  - "documents [Office development in Visual Studio], custom XML parts"
ms.assetid: e305a3d6-3a0e-4e72-ab8c-6a87a3590068
caps.latest.revision: 27
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# How to: Add Custom XML Parts to Document-Level Customizations
  You can store XML data in a Microsoft Office Excel workbook or Microsoft Office Word document by creating a custom XML part in a document-level customization. For more information, see [Custom XML Parts Overview](../vsto/custom-xml-parts-overview.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  Visual Studio does not provide document-level projects for Microsoft Office PowerPoint. For information about adding a custom XML part to a PowerPoint presentation by using an VSTO Add-in, see [How to: Add Custom XML Parts to Documents by Using VSTO Add-Ins](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).  
  
### To add a custom XML part to an Excel workbook  
  
1.  Add a new <xref:Microsoft.Office.Core.CustomXMLPart> object to the <xref:Microsoft.Office.Core.CustomXMLParts> collection in the workbook. The <xref:Microsoft.Office.Core.CustomXMLPart> contains the XML string that you want to store in the workbook.  
  
     [!code-csharp[Trin_AddCustomXmlPartExcelDocLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartExcelDocLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartExcelDocLevel/ThisWorkbook.vb#1)]  
  
2.  Add the `AddCustomXmlPartToWorkbook` method to the `ThisWorkbook` class in a document-level project for Excel.  
  
3.  Call the method from other code in your project. For example, to create the custom XML part when the user opens the workbook, call the method from the `ThisWorkbook_Startup` event handler.  
  
### To add a custom XML part to a Word document  
  
1.  Add a new <xref:Microsoft.Office.Core.CustomXMLPart> object to the <xref:Microsoft.Office.Core.CustomXMLParts> collection in the document. The <xref:Microsoft.Office.Core.CustomXMLPart> contains the XML string that you want to store in the document.  
  
     [!code-vb[Trin_AddCustomXmlPartWordDocLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordDocLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordDocLevel/ThisDocument.cs#1)]  
  
2.  Add the `AddCustomXmlPartToDocument` method to the `ThisDocument` class in a document-level project for Word.  
  
3.  Call the method from other code in your project. For example, to create the custom XML part when the user opens the document, call the method from the `ThisDocument_Startup` event handler.  
  
## Robust Programming  
 For simplicity, this example uses an XML string that is defined as a local variable in the method. Typically, you should obtain the XML from an external source, such as a file or a database.  
  
## See Also  
 [Custom XML Parts Overview](../vsto/custom-xml-parts-overview.md)   
 [How to: Add Custom XML Parts to Documents by Using VSTO Add-Ins](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
  