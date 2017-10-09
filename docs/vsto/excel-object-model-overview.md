---
title: "Excel Object Model Overview | Microsoft Docs"
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
  - "Worksheet object"
  - "Range object"
  - "object models [Office development in Visual Studio], Excel"
  - "object models [Office development in Visual Studio], Office"
  - "Workbook class"
  - "objects [Office development in Visual Studio], Office object models"
  - "Excel object model"
  - "Office object models"
ms.assetid: e4b2e46b-ea6c-4a88-a416-a7d4f495fc33
caps.latest.revision: 66
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# Excel Object Model Overview
  To develop solutions that use Microsoft Office Excel, you can interact with the objects provided by the Excel object model. This topic introduces the most important objects:  
  
-   <xref:Microsoft.Office.Interop.Excel.Application>  
  
-   <xref:Microsoft.Office.Interop.Excel.Workbook>  
  
-   <xref:Microsoft.Office.Interop.Excel.Worksheet>  
  
-   <xref:Microsoft.Office.Interop.Excel.Range>  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 The object model closely follows the user interface. The <xref:Microsoft.Office.Interop.Excel.Application> object represents the entire application, and each <xref:Microsoft.Office.Interop.Excel.Workbook> object contains a collection of `Worksheet` objects. From there, the major abstraction that represents cells is the <xref:Microsoft.Office.Interop.Excel.Range> object, which enables you to work with individual cells or groups of cells.  
  
 In addition to the Excel object model, Office projects in Visual Studio provide *host items* and *host controls* that extend some objects in the Excel object model. Host items and host controls behave like the Excel objects they extend, but they also have additional functionality such as data-binding capabilities and extra events. For more information, see [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md) and [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
 This topic provides a brief overview of the Excel object model. For resources where you can learn more about the entire Excel object model, see [Using the Excel Object Model Documentation](#ExcelOMDocumentation).  
  
 ![link to video](../vsto/media/playvideo.gif "link to video") For a related video demonstration, see [How Do I: Use Event Handlers in an Excel 2007 Add-in?](http://go.microsoft.com/fwlink/?LinkID=130291), and [How Do I: Use Shapes to Create a Bubble Chart in Excel?](http://go.microsoft.com/fwlink/?LinkID=130313).  
  
## Accessing Objects in an Excel Project  
 When you create a new VSTO Add-in project for Excel, Visual Studio automatically creates a ThisAddIn.vb or ThisAddIn.cs code file. You can access the Application object by using `Me.Application` or `this.Application`.  
  
 When you create a new document-level project for Excel, you have the option of creating a new Excel Workbook or Excel Template project. Visual Studio automatically creates the following code files in your new Excel project for both workbook and template projects.  
  
|Visual Basic|C#|  
|------------------|---------|  
|ThisWorkbook.vb|ThisWorkbook.cs|  
|Sheet1.vb|Sheet1.cs|  
|Sheet2.vb|Sheet2.cs|  
|Sheet3.vb|Sheet3.cs|  
  
 You can use the `Globals` class in your project to access `ThisWorkbook`, `Sheet1`, `Sheet2`, or `Sheet3` from outside of the respective class. For more information, see [Global Access to Objects in Office Projects](../vsto/global-access-to-objects-in-office-projects.md). The following example calls the <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> method of `Sheet1` regardless of whether the code is placed in one of the `Sheet`*n* classes or the `ThisWorkbook` class.  
  
 [!code-csharp[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#82)]  
  
 Because the data in an Excel document is highly structured, the object model is hierarchical and straightforward. Excel provides hundreds of objects with which you might want to interact, but you can get a good start on the object model by focusing on a very small subset of the available objects. These objects include the following four:  
  
-   Application  
  
-   Workbook  
  
-   Worksheet  
  
-   Range  
  
 Much of the work done with Excel centers around these four objects and their members.  
  
### Application Object  
 The Excel <xref:Microsoft.Office.Interop.Excel.Application> object represents the Excel application itself. The <xref:Microsoft.Office.Interop.Excel.Application> object exposes a great deal of information about the running application, the options applied to that instance, and the current user objects open within the instance.  
  
> [!NOTE]  
>  You should not set the <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> property of the <xref:Microsoft.Office.Interop.Excel.Application> object in Excel to **false**. Setting this property to false prevents Excel from raising any events, including the events of host controls.  
  
### Workbook Object  
 The <xref:Microsoft.Office.Interop.Excel.Workbook> object represents a single workbook within the Excel application.  
  
 The Office development tools in Visual Studio extends the <xref:Microsoft.Office.Interop.Excel.Workbook> object by providing the <xref:Microsoft.Office.Tools.Excel.Workbook> type. This type gives you access to all features of a <xref:Microsoft.Office.Interop.Excel.Workbook> object. For more information, see [Workbook Host Item](../vsto/workbook-host-item.md).  
  
### Worksheet Object  
 The <xref:Microsoft.Office.Interop.Excel.Worksheet> object is a member of the <xref:Microsoft.Office.Interop.Excel.Worksheets> collection. Many of the properties, methods, and events of the <xref:Microsoft.Office.Interop.Excel.Worksheet> are identical or similar to members provided by the <xref:Microsoft.Office.Interop.Excel.Application> or <xref:Microsoft.Office.Interop.Excel.Workbook> objects.  
  
 Excel provides a <xref:Microsoft.Office.Interop.Excel.Sheets> collection as a property of a <xref:Microsoft.Office.Interop.Excel.Workbook> object. Each member of the <xref:Microsoft.Office.Interop.Excel.Sheets> collection is either a <xref:Microsoft.Office.Interop.Excel.Worksheet> or a <xref:Microsoft.Office.Interop.Excel.Chart> object.  
  
 The Office development tools in Visual Studio extend the <xref:Microsoft.Office.Interop.Excel.Worksheet> object by providing the <xref:Microsoft.Office.Tools.Excel.Worksheet> type. This type gives you access to all features of a <xref:Microsoft.Office.Interop.Excel.Worksheet> object, as well as new features such as the ability to host managed controls and handle new events. For more information, see [Worksheet Host Item](../vsto/worksheet-host-item.md).  
  
### Range Object  
 The <xref:Microsoft.Office.Interop.Excel.Range> object is the object you will use most within your Excel applications. Before you can manipulate any region within Excel, you must express it as a <xref:Microsoft.Office.Interop.Excel.Range> object and work with methods and properties of that range. A <xref:Microsoft.Office.Interop.Excel.Range> object represents a cell, a row, a column, a selection of cells that contains one or more blocks of cells, which might or might not be contiguous, or even a group of cells on multiple sheets.  
  
 Visual Studio extends the <xref:Microsoft.Office.Interop.Excel.Range> object by providing the <xref:Microsoft.Office.Tools.Excel.NamedRange> and <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> types. These types have most of the same features as a <xref:Microsoft.Office.Interop.Excel.Range> object, as well as new features such as the data binding capability and new events. For more information, see [NamedRange Control](../vsto/namedrange-control.md) and [XmlMappedRange Control](../vsto/xmlmappedrange-control.md).  
  
##  <a name="ExcelOMDocumentation"></a> Using the Excel Object Model Documentation  
 For complete information about the Excel object model, you can refer to the Excel primary interop assembly (PIA) reference and the VBA object model reference.  
  
### Primary Interop Assembly Reference  
 The Excel PIA reference documentation describes the types in the primary interop assembly for Excel. This documentation is available from the following location: [Excel 2010 Primary Interop Assembly Reference](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
 For more information about the design of the Excel PIA, such as the differences between classes and interfaces in the PIA and how events in the PIA are implemented, see [Overview of Classes and Interfaces in the Office Primary Interop Assemblies](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
### VBA Object Model Reference  
 The VBA object model reference documents the Excel object model as it is exposed to Visual Basic for Applications (VBA) code. For more information, see [Excel 2010 Object Model Reference](http://go.microsoft.com/fwlink/?LinkId=199768).  
  
 All of the objects and members in the VBA object model reference correspond to types and members in the Excel PIA. For example, the Worksheet object in the VBA object model reference corresponds to the <xref:Microsoft.Office.Interop.Excel.Worksheet> object in the Excel PIA. Although the VBA object model reference provides code examples for most properties, methods, and events, you must translate the VBA code in this reference to Visual Basic or Visual C# if you want to use them in an Excel project that you create by using Visual Studio.  
  
### Related Topics  
  
|Title|Description|  
|-----------|-----------------|  
|[Excel Solutions](../vsto/excel-solutions.md)|Explains how you can create document-level customizations and VSTO Add-ins for Microsoft Office Excel.|  
|[Working with Ranges](../vsto/working-with-ranges.md)|Provides examples that show how to perform common tasks with ranges.|  
|[Working with Worksheets](../vsto/working-with-worksheets.md)|Provides examples that show how to perform common tasks with worksheets.|  
|[Working with Workbooks](../vsto/working-with-workbooks.md)|Provides examples that show how to perform common tasks with workbooks.|  
  
  