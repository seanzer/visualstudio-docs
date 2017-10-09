---
title: "Walkthrough: Changing Worksheet Formatting Using CheckBox Controls | Microsoft Docs"
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
  - "worksheets, changing formatting using managed controls"
  - "worksheets, check box controls"
  - "controls [Office development in Visual Studio], adding to worksheets"
ms.assetid: 4be79613-50a0-428e-9816-aadbc098272a
caps.latest.revision: 70
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# Walkthrough: Changing Worksheet Formatting Using CheckBox Controls
  This walkthrough shows the basics of using check boxes on a Microsoft Office Excel worksheet to change formatting. You will use Office development tools in Visual Studio to create and add code to your project. To see the result as a completed sample, see the Excel Controls Sample at [Office Development Samples and Walkthroughs](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 During this walkthrough, you will learn how to:  
  
-   Add text and controls to a worksheet.  
  
-   Format the text when an option is selected.  
  
-   Test your project.  
  
> [!NOTE]  
>  Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions. The Visual Studio edition that you have and the settings that you use determine these elements. For more information, see [Personalize the Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## Prerequisites  
 You need the following components to complete this walkthrough:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] or [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## Creating the Project  
 In this step, you will create an Excel Workbook project by using Visual Studio.  
  
#### To create a new project  
  
1.  Create an Excel Workbook project with the name **My Excel Formatting**. Make sure that **Create a new document** is selected. For more information, see [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio opens the new Excel workbook in the designer and adds the **My Excel Formatting** project to **Solution Explorer**.  
  
## Adding Text and Controls to the Worksheet  
 For this walkthrough, you will need three <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> controls and some text in a <xref:Microsoft.Office.Tools.Excel.NamedRange> control.  
  
#### To add three check boxes  
  
1.  Verify that the workbook is open in the Visual Studio designer and that `Sheet1` is open.  
  
2.  From the **Common Controls** tab of the **Toolbox**, drag a <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> control to or near cell **B2** in **Sheet1**.  
  
3.  From the **View** menu, select **Properties** window.  
  
4.  Be sure that **Checkbox1** is visible in the object name list box of the **Properties** window, and change the following properties:  
  
    |Property|Value|  
    |--------------|-----------|  
    |**Name**|**applyBoldFont**|  
    |**Text**|**Bold**|  
  
5.  Drag a second check box on or near cell **B4** and change the following properties:  
  
    |Property|Value|  
    |--------------|-----------|  
    |**Name**|**applyItalicFont**|  
    |**Text**|**Italic**|  
  
6.  Drag a third check box on or near cell **B6** and change the following properties:  
  
    |Property|Value|  
    |--------------|-----------|  
    |**Name**|**applyUnderlineFont**|  
    |**Text**|**Underline**|  
  
7.  Select all three check box controls while holding the CTRL key.  
  
8.  In the Arrange Group of the Format tab in Excel, click **Align**, and then click **Align Left**.  
  
     The three check box controls are aligned on the left side, at the position of the first control you selected.  
  
     Next, you will drag a <xref:Microsoft.Office.Tools.Excel.NamedRange> control to the worksheet.  
  
    > [!NOTE]  
    >  You can also add the <xref:Microsoft.Office.Tools.Excel.NamedRange> control by typing **textFont** into the **Name** box.  
  
#### To add text to a NamedRange control  
  
1.  From the **Excel Controls** tab of the toolbox, drag a <xref:Microsoft.Office.Tools.Excel.NamedRange> control to cell **B9**.  
  
2.  Verify that **$B$9** appears in the editable text box, and that cell **B9** is selected. If it is not, click cell **B9** to select it.  
  
3.  Click **OK**.  
  
4.  Cell **B9** becomes a range named `NamedRange1`.  
  
     There is no visible indication on the worksheet, but `NamedRange1` appears in the **Name box** (just above the worksheet on the left side) when cell **B9** is selected.  
  
5.  Be sure that **NamedRange1** is visible in the object name list box of the **Properties** window, and change the following properties:  
  
    |Property|Value|  
    |--------------|-----------|  
    |**Name**|**textFont**|  
    |**Value2**|**Click a check box to change the formatting of this text.**|  
  
 Next, write the code to format the text when an option is selected.  
  
## Formatting the Text When an Option is Selected  
 In this section, you will write code so that when the user selects a formatting option, the format of the text in the worksheet is changed.  
  
#### To change formatting when a check box is selected  
  
1.  Right-click **Sheet1**, and then click **View Code** on the shortcut menu.  
  
2.  Add the following code to the <xref:System.Windows.Forms.Control.Click> event handler of the `applyBoldFont` check box:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]  
  
3.  Add the following code to the <xref:System.Windows.Forms.Control.Click> event handler of the `applyItalicFont` check box:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]  
  
4.  Add the following code to the <xref:System.Windows.Forms.Control.Click> event handler of the `applyUnderlineFont` check box:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]  
  
5.  In C#, you must add event handlers for the check boxes to the <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> event as shown below. For information on creating event handlers, see [How to: Create Event Handlers in Office Projects](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]  
  
## Testing the Application  
 You can now test your workbook to make sure that the text is formatted correctly when you select or clear a check box.  
  
#### To test your workbook  
  
1.  Press F5 to run your project.  
  
2.  Select or clear a check box.  
  
3.  Confirm that the text is formatted correctly.  
  
## Next Steps  
 This walkthrough shows the basics of using check boxes and formatting text on Excel worksheets. Here are some tasks that might come next:  
  
-   Deploying the project. For more information, see [Deploying an Office Solution by Using ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
-   Using a button to populate a text box. For more information, see [Walkthrough: Displaying Text in a Text Box in a Worksheet Using a Button](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  
  
## See Also  
 [Walkthroughs Using Excel](../vsto/walkthroughs-using-excel.md)   
 [NamedRange Control](../vsto/namedrange-control.md)   
 [Limitations of Windows Forms Controls on Office Documents](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  