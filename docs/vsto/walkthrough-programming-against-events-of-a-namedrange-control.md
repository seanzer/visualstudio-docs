---
title: "Walkthrough: Programming Against Events of a NamedRange Control | Microsoft Docs"
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
  - "ranges, programming against events"
  - "worksheets, changing cell values"
  - "NamedRange control, events"
  - "worksheets, events"
  - "worksheets, automating"
ms.assetid: b69676f9-23b2-4ed6-83ab-8868c3f10948
caps.latest.revision: 57
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# Walkthrough: Programming Against Events of a NamedRange Control
  This walkthrough demonstrates how to add a <xref:Microsoft.Office.Tools.Excel.NamedRange> control to a Microsoft Office Excel worksheet and program against its events using by using Office development tools in Visual Studio.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 During this walkthrough, you will learn how to:  
  
-   Add a <xref:Microsoft.Office.Tools.Excel.NamedRange> control to a worksheet.  
  
-   Program against <xref:Microsoft.Office.Tools.Excel.NamedRange> control events.  
  
-   Test your project.  
  
> [!NOTE]  
>  Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions. The Visual Studio edition that you have and the settings that you use determine these elements. For more information, see [Personalize the Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## Prerequisites  
 You need the following components to complete this walkthrough:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] or [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## Creating the Project  
 In this step, you will create an Excel workbook project using Visual Studio.  
  
#### To create a new project  
  
1.  Create an Excel Workbook project with the name **My Named Range Events**. Make sure that **Create a new document** is selected. For more information, see [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio opens the new Excel workbook in the designer and adds the **My Named Range Events** project to **Solution Explorer**.  
  
## Adding Text and Named Ranges to the Worksheet  
 Because host controls are extended Office objects, you can add them to your document in the same manner you would add the native object. For example, you can add an Excel <xref:Microsoft.Office.Tools.Excel.NamedRange> control to a worksheet by opening the **Insert** menu, pointing to **Name**, and choosing **Define**. You can also add a <xref:Microsoft.Office.Tools.Excel.NamedRange> control by dragging it from the **Toolbox** onto the worksheet.  
  
 In this step, you will add two named range controls to the worksheet using the **Toolbox**, and then add text to the worksheet.  
  
#### To add a range to your worksheet  
  
1.  Verify that the **My Named Range Events.xlsx** workbook is open in the Visual Studio designer, with `Sheet1` displayed.  
  
2.  From the **Excel Controls** tab of the Toolbox, drag a <xref:Microsoft.Office.Tools.Excel.NamedRange> control to cell **A1** in `Sheet1`.  
  
     The **Add NamedRange Control** dialog box appears.  
  
3.  Verify that **$A$1** appears in the editable text box, and that cell **A1** is selected. If it is not, click cell **A1** to select it.  
  
4.  Click **OK**.  
  
     Cell **A1** becomes a range named `namedRange1`. There is no visible indication on the worksheet, but `namedRange1` appears in the **Name** box (located just above the worksheet on the left side) when cell **A1** is selected.  
  
5.  Add another <xref:Microsoft.Office.Tools.Excel.NamedRange> control to cell **B3**.  
  
6.  Verify that **$B$3** appears in the editable text box, and that cell **B3** is selected. If it is not, click cell **B3** to select it.  
  
7.  Click **OK**.  
  
     Cell **B3** becomes a range named `namedRange2`.  
  
#### To add text to your worksheet  
  
1.  In Cell **A1**, type the following text:  
  
     **This is an example of a NamedRange control.**  
  
2.  In Cell **A3** (to the left of `namedRange2`), type the following text:  
  
     **Events:**  
  
 In the following sections, you will write code that inserts text into `namedRange2` and modifies properties of the `namedRange2` control in response to the <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>, <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>, and <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> events of `namedRange1`.  
  
## Adding Code to Respond to the BeforeDoubleClick Event  
  
#### To insert text into NamedRange2 based on the BeforeDoubleClick event  
  
1.  In **Solution Explorer**, right-click **Sheet1.vb** or **Sheet1.cs** and select **View Code**.  
  
2.  Add code so the `namedRange1_BeforeDoubleClick` event handler looks like the following:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#24)]  
  
3.  In C#, you must add event handlers for the named range as shown in the <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> event below. For information on creating event handlers, see [How to: Create Event Handlers in Office Projects](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#25)]  
  
## Adding Code to Respond to the Change Event  
  
#### To insert text into namedRange2 based on the Change event  
  
1.  Add code so the `NamedRange1_Change` event handler looks like the following:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#26)]  
  
    > [!NOTE]  
    >  Because double-clicking a cell in an Excel range enters edit mode, a <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> event occurs when the selection is moved outside of the range even if no changes to text occurred.  
  
## Adding Code to Respond to the SelectionChange Event  
  
#### To insert text into namedRange2 based on the SelectionChange event  
  
1.  Add code so the **NamedRange1_SelectionChange** event handler looks like the following:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#27)]  
  
    > [!NOTE]  
    >  Because double-clicking a cell in an Excel range causes the selection to move into the range, a <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> event occurs before the <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> event occurs.  
  
## Testing the Application  
 Now you can test your workbook to verify that text describing the events of a <xref:Microsoft.Office.Tools.Excel.NamedRange> control is inserted into another named range when the events are raised.  
  
#### To test your document  
  
1.  Press F5 to run your project.  
  
2.  Place your cursor in `namedRange1`, and verify that the text regarding the <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> event is inserted and that a comment is inserted into the worksheet.  
  
3.  Double click inside `namedRange1`, and verify that the text regarding <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> events is inserted with red italicized text in `namedRange2`.  
  
4.  Click outside of `namedRange1` and note that the change event occurs when exiting edit mode even though no change to the text was made.  
  
5.  Change the text within `namedRange1`.  
  
6.  Click outside of `namedRange1`, and verify that the text regarding <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> event is inserted with blue text into `namedRange2`.  
  
## Next Steps  
 This walkthrough shows the basics of programming against events of a <xref:Microsoft.Office.Tools.Excel.NamedRange> control. Here is a task that might come next:  
  
-   Deploying the project. For more information, see [Deploying an Office Solution](../vsto/deploying-an-office-solution.md).  
  
## See Also  
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md)   
 [NamedRange Control](../vsto/namedrange-control.md)   
 [How to: Resize NamedRange Controls](../vsto/how-to-resize-namedrange-controls.md)   
 [How to: Add NamedRange Controls to Worksheets](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [How to: Create Event Handlers in Office Projects](../vsto/how-to-create-event-handlers-in-office-projects.md)  
  
  