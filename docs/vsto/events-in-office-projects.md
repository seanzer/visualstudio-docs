---
title: "Events in Office Projects | Microsoft Docs"
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
  - "Sheet1_Startup"
  - "ThisDocument_Shutdown"
  - "ThisDocument_Startup"
  - "application-level add-ins [Office development in Visual Studio], events"
  - "event handlers [Office development in Visual Studio]"
  - "ThisWorkbook_Startup"
  - "Sheet2_Startup"
  - "ThisWorkbook_Shutdown"
  - "document-level customizations [Office development in Visual Studio], events"
  - "Sheet2_Shutdown"
  - "Startup event"
  - "Sheet3_Shutdown"
  - "add-ins [Office development in Visual Studio], events"
  - "Shutdown event"
  - "ThisAddIn_Startup"
  - "Sheet3_Startup"
  - "Startup method [Office development in Visual Studio]"
  - "Shutdown method [Office development in Visual Studio]"
  - "Sheet1_Shutdown"
  - "events [Office development in Visual Studio]"
  - "ThisAddIn_Shutdown"
ms.assetid: 666d7f23-ef85-4f2e-9cd3-258df5bdc6fd
caps.latest.revision: 51
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# Events in Office Projects
  Each Office project template automatically generates several event handlers. The event handlers for document-level customizations are slightly different from event handlers for VSTO Add-ins.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Document-Level Projects  
 Visual Studio provides generated code behind new or existing documents or worksheets in document-level customizations. This code raises two different events: **Startup** and **Shutdown**.  
  
### Startup Event  
 The **Startup** event is raised for each of the host items (document, workbook or worksheet) after the document is running and all the initialization code in the assembly has been run. It is the last thing to run in the constructor of the class that your code is running in. For more information about host items, see [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
 When you create a document-level project, Visual Studio creates event handlers for the **Startup** event in the generated code files:  
  
-   For Microsoft Office Word projects, the event handler is named `ThisDocument_Startup`.  
  
-   For Microsoft Office Excel projects, the event handlers have the following names:  
  
    -   `Sheet1_Startup`  
  
    -   `Sheet2_Startup`  
  
    -   `Sheet3_Startup`  
  
    -   `ThisWorkbook_Startup`  
  
### Shutdown Event  
 The **Shutdown** event is raised for each of the host items (document or worksheet) when the application domain that your code is loaded in is about to unload. It is the last thing to be called in the class as it unloads.  
  
 When you create a document-level project, Visual Studio creates event handlers for the **Shutdown** event in the generated code files:  
  
-   For Microsoft Office Word projects, the event handler is named `ThisDocument_Shutdown`.  
  
-   For Microsoft Office Excel projects, the event handlers have the following names:  
  
    -   `Sheet1_Shutdown`  
  
    -   `Sheet2_Shutdown`  
  
    -   `Sheet3_Shutdown`  
  
    -   `ThisWorkbook_Shutdown`  
  
> [!NOTE]  
>  Do not programmatically remove controls during the **Shutdown** event handler of the document. The UI elements of the document are no longer available when the **Shutdown** event occurs. If you want to remove controls before the application closes, add your code to another event handler, such as **BeforeClose** or **BeforeSave**.  
  
### Event Handler Method Declarations  
 Every event handler method declaration has the same arguments passed to it: *sender* and *e*. In Excel, the *sender* argument refers to the sheet, such as `Sheet1` or `Sheet2`; in Word, the *sender* argument refers to the document. The *e* argument refers to the standard arguments for an event, which are not used in this case.  
  
 The following code example shows the default event handlers in document-level projects for Word.  
  
 [!code-vb[Trin_VstcoreWordAutomation#121](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#121)]
 [!code-csharp[Trin_VstcoreWordAutomation#121](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#121)]  
  
 The following code example shows the default event handlers in document-level projects for Excel.  
  
> [!NOTE]  
>  The following code example shows the event handlers in the `Sheet1` class. The names of the event handlers in other host item classes correspond to the class name. For example, in the `Sheet2` class, the **Startup** event handler is named `Sheet2_Startup`. In the `ThisWorkbook` class, the **Startup** event handler is named `ThisWorkbook_Startup`.  
  
 [!code-csharp[Trin_VstcoreExcelAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#83)]
 [!code-vb[Trin_VstcoreExcelAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#83)]  
  
### Order of Events in Document-Level Excel Projects  
 The **Startup** event handlers in Excel projects are called in this order:  
  
1.  `ThisWorkbook_Startup`.  
  
2.  `Sheet1_Startup`.  
  
3.  `Sheet2_Startup`.  
  
4.  `Sheet3_Startup`.  
  
5.  Other sheets in order.  
  
 The **Shutdown** event handlers in a workbook solution are called in this order:  
  
1.  `ThisWorkbook_Shutdown`.  
  
2.  `Sheet1_Shutdown`.  
  
3.  `Sheet2_Shutdown`.  
  
4.  `Sheet3_Shutdown`.  
  
5.  Other sheets in order.  
  
 The order is determined when the project is compiled. If the user rearranges the sheets at run time, it does not change the order that the events are raised the next time the workbook is opened or closed.  
  
## VSTO Add-in Projects  
 Visual Studio provides generated code in VSTO Add-ins. This code raises two different events: <xref:Microsoft.Office.Tools.AddInBase.Startup> and <xref:Microsoft.Office.Tools.AddInBase.Shutdown>.  
  
### Startup Event  
 The <xref:Microsoft.Office.Tools.AddIn.Startup> event is raised after the VSTO Add-in is loaded and all the initialization code in the assembly has been run. This event is handled by the `ThisAddIn_Startup` method in the generated code file.  
  
 Code in the `ThisAddIn_Startup` event handler is the first user code to run, unless your VSTO Add-in overrides the <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> method. In this case, the `ThisAddIn_Startup` event handler is called after <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>.  
  
 Don't add code in the `ThisAdd-In_Startup` event handler if the code requires a document to be open. Instead, add that code to an event that the Office application raises when a user creates or opens a document. For more information, see [Accessing a Document When the Office Application Starts](../vsto/programming-vsto-add-ins.md#AccessingDocuments).  
  
 For more information about the startup sequence of VSTO Add-ins, see [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
### Shutdown Event  
 The <xref:Microsoft.Office.Tools.AddInBase.Shutdown> event is raised when the application domain that your code is loaded in is about to be unloaded. This event is handled by the `ThisAddIn_Shutdown` method in the generated code file. This event handler is the last user code to run when the VSTO Add-in is unloaded.  
  
#### Shutdown Event in Outlook VSTO Add-ins  
 The <xref:Microsoft.Office.Tools.AddInBase.Shutdown> event is raised only when the user disables the VSTO Add-in by using the COM Add-ins dialog box in Outlook. It is not raised when Outlook exits. If you have code that must run when Outlook exits, handle either of the following events:  
  
-   The <xref:Microsoft.Office.Interop.Outlook.ApplicationEvents_11_Event.Quit> event of the <xref:Microsoft.Office.Interop.Outlook.Application> object.  
  
-   The <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> event of the <xref:Microsoft.Office.Interop.Outlook.Explorer> object.  
  
> [!NOTE]  
>  You can force Outlook to raise the <xref:Microsoft.Office.Tools.AddInBase.Shutdown> event when it exits by modifying the registry. However, if an administrator reverts this setting, any code that you add to the `ThisAddIn_Shutdown` method no longer runs when Outlook exits. For more information, see [Shutdown Changes for Outlook 2010](http://go.microsoft.com/fwlink/?LinkID=184614).  
  
## See Also  
 [Developing Office Solutions](../vsto/developing-office-solutions.md)   
 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Office Project Templates Overview](../vsto/office-project-templates-overview.md)  
  
  