---
title: "How to: Programmatically Cache a Data Source in an Office Document | Microsoft Docs"
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
  - "Office applications [Office development in Visual Studio], data"
  - "datasets [Office development in Visual Studio], caching"
  - "StartCaching method"
  - "data caching [Office development in Visual Studio], programmatically"
  - "data [Office development in Visual Studio], caching"
ms.assetid: 70b3fc06-7534-407e-898b-36f84e9a7516
caps.latest.revision: 43
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# How to: Programmatically Cache a Data Source in an Office Document
  You can programmatically add a data object to the data cache in a document by calling the `StartCaching` method of a host item, such as a <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>, or <xref:Microsoft.Office.Tools.Excel.Worksheet>. Remove a data object from the data cache by calling the `StopCaching` method of a host item.  
  
 The `StartCaching` method and the `StopCaching` method are both private, but they appear in IntelliSense.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 When you use the `StartCaching` method to add a data object to the data cache, the data object does not need to be declared with the <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> attribute. However, the data object must meet certain requirements to be added to the data cache. For more information, see [Caching Data](../vsto/caching-data.md).  
  
### To programmatically cache a data object  
  
1.  Declare the data object at the class level, not inside a method. This example assumes that you are declaring a <xref:System.Data.DataSet> named `dataSet1` that you want to cache programmatically.  
  
     [!code-csharp[Trin_VstcoreDataExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#12)]  
  
2.  Instantiate the data object, and then call the `StartCaching` method of the document or worksheet instance and pass in the name of the data object.  
  
     [!code-csharp[Trin_VstcoreDataExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#13)]  
  
### To stop caching a data object  
  
1.  Call the `StopCaching` method of the document or worksheet instance and pass in the name of the data object. This example assumes that you have a <xref:System.Data.DataSet> named `dataSet1` that you want to stop caching.  
  
     [!code-csharp[Trin_VstcoreDataExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#14)]  
  
    > [!NOTE]  
    >  Do not call `StopCaching` from the event handler for the `Shutdown` event of a document or worksheet. By the time the `Shutdown` event is raised, it is too late to modify the data cache. For more information about the `Shutdown` event, see [Events in Office Projects](../vsto/events-in-office-projects.md).  
  
## See Also  
 [Caching Data](../vsto/caching-data.md)   
 [How to: Cache Data for Use Offline or on a Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [How to: Cache Data in a Password-Protected Document](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Saving Data](/visualstudio/data-tools/saving-data)  
  
  