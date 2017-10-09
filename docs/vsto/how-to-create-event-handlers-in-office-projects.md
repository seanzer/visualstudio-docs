---
title: "How to: Create Event Handlers in Office Projects | Microsoft Docs"
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
  - "Visual Basic [Office development in Visual Studio], event handlers"
  - "event handlers [Office development in Visual Studio]"
  - "Visual C# [Office development in Visual Studio], event handlers"
  - "events [Office development in Visual Studio]"
ms.assetid: 2cfd6a45-4c25-4431-b4fc-e0f2c0a72e54
caps.latest.revision: 31
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# How to: Create Event Handlers in Office Projects
  There are several ways to create event handlers in Visual Basic and C#. In design view, you can create the default event handlers for controls by double-clicking the control, or use the events pane of the **Properties** window to create handlers for any event on the control. However, if you are in Code view, you may not want to switch to Design view to create an event handler.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### To create an event handler in Visual Basic  
  
1.  From the **Class Name** drop-down list at the top of the Code Editor, select the object that you want to create an event handler for.  
  
    > [!NOTE]  
    >  If you want to create event handlers for `ThisDocument` or `ThisWorkbook`, you must select **(ThisDocument Events)** or **(ThisWorkbook Events)** in the **Class Name** drop-down list  
  
2.  From the **Method Name** drop-down list at the top of the Code Editor, select the event.  
  
     Visual Studio creates the event handler and moves the insertion point to the newly created event handler. If the event handler already exists, the insertion point moves to the existing event handler.  
  
### To create an event handler in C#  
  
1.  Create the event delegate in the **Startup** event of the class by typing the qualified event name followed by a space, and then typing **+=** with no space afterwards. For example:  
  
     `this.<object name>.<event name> +=`  
  
2.  At the end of the line of code, press the TAB key twice.  
  
     Visual Studio automatically completes the line of code, creates the event handler, and moves the insertion point to the newly created event handler.  
  
## See Also  
 [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)   
 [Walkthrough: Programming Against Events of a NamedRange Control](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [Building Office Solutions](../vsto/building-office-solutions.md)  
  
  