---
title: "Walkthrough: Changing Document Formatting Using CheckBox Controls | Microsoft Docs"
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
  - "Word documents, changing formatting using controls"
  - "documents [Office development in Visual Studio], formatting"
  - "check boxes, Word documents"
  - "documents [Office development in Visual Studio], check box controls"
  - "controls [Office development in Visual Studio], adding to documents"
ms.assetid: 3740e41d-a57e-43bb-87e7-6e5481ef290b
caps.latest.revision: 70
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# Walkthrough: Changing Document Formatting Using CheckBox Controls
  This walkthrough demonstrates how to use Windows Forms controls in a document-level customization for Microsoft Office Word to change text formatting.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 This walkthrough illustrates the following tasks:  
  
-   Adding text and a control to the document in a document-level project at design time.  
  
-   Formatting the text when an option is selected.  
  
 To see the result as a completed sample, see the Word Controls Sample at [Office Development Samples and Walkthroughs](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisites  
 You need the following components to complete this walkthrough:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] or [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## Creating the Project  
 The first step is to create a Word Document project.  
  
#### To create a new project  
  
1.  Create a Word Document project with the name **My Word Formatting**. In the wizard, select **Create a new document**.  
  
     For more information, see [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio opens the new Word document in the designer and adds the **My Word Formatting** project to **Solution Explorer**.  
  
## Adding Text and Controls to the Word Document  
 For this walkthrough, add three check boxes and some text in a <xref:Microsoft.Office.Tools.Word.Bookmark> control to the Word document. The check boxes will present options to the user for formatting the text.  
  
#### To add three check boxes  
  
1.  Verify that the document is open in the Visual Studio designer.  
  
2.  From the **Common Controls** tab of the **Toolbox**, drag the first <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> control to the document.  
  
3.  In the **Properties** window, change the following properties.  
  
    |Property|Value|  
    |--------------|-----------|  
    |**Name**|**applyBoldFont**|  
    |**Text**|**Bold**|  
  
4.  Press **Enter** to move the insertion point below the first check box.  
  
5.  Add a second check box to the document below the `ApplyBoldFont` check box and change the following properties.  
  
    |Property|Value|  
    |--------------|-----------|  
    |**Name**|**applyItalicFont**|  
    |**Text**|**Italic**|  
  
6.  Press **Enter** to move the insertion point below the second check box.  
  
7.  Add a third check box to the document below the `ApplyItalicFont` check box and change the following properties.  
  
    |Property|Value|  
    |--------------|-----------|  
    |**Name**|**applyUnderlineFont**|  
    |**Text**|**Underline**|  
  
#### To add text and a Bookmark control  
  
1.  Move the insertion point below the check box controls and type the following text:  
  
     **Click a check box to change the formatting of this text.**  
  
2.  From the **Word Controls** tab of the **Toolbox**, drag a <xref:Microsoft.Office.Tools.Word.Bookmark> control to the document.  
  
     The **Add Bookmark Control** dialog box appears.  
  
3.  Select the text you added to the document and click **OK**.  
  
     A <xref:Microsoft.Office.Tools.Word.Bookmark> control named **Bookmark1** is added to the selected text in the document.  
  
4.  In the **Properties** window, change the value of the **(Name)** property to **fontText.**  
  
 Next, write the code to format the text when a check box is checked or cleared.  
  
## Formatting the Text When a Check box is Checked or Cleared  
 When the user selects a formatting option, change the format of the text in the document.  
  
#### To change formatting when a check box is selected  
  
1.  Right-click `ThisDocument` in **Solution Explorer**, and then click **View Code** on the shortcut menu.  
  
2.  For C# only, add the following constants to the **ThisDocument** class.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#2)]  
  
3.  Add the following code to the <xref:System.Windows.Forms.Control.Click> event handler of the `applyBoldFont` check box.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#3)]  
  
4.  Add the following code to the <xref:System.Windows.Forms.Control.Click> event handler of the `applyItalicFont` check box.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#4)]  
  
5.  Add the following code to the <xref:System.Windows.Forms.Control.Click> event handler of the `applyUnderlineFont` check box.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#5)]  
  
6.  In C#, you must add event handlers for the text boxes to the <xref:Microsoft.Office.Tools.Word.Document.Startup> event. For information about how to create event handlers, see [How to: Create Event Handlers in Office Projects](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#6)]  
  
## Testing the Application  
 You can now test your document to verify that the text is formatted correctly when you select or clear a check box.  
  
#### To test your document  
  
1.  Press F5 to run your project.  
  
2.  Select or clear a check box.  
  
3.  Confirm that the text is formatted correctly.  
  
## Next Steps  
 This walkthrough shows the basics of using check boxes and programmatically changing text formatting on Word documents. Here are some tasks that might come next:  
  
-   Use a button to populate a text box. For more information, see [Walkthrough: Displaying Text in a Text Box in a Document Using a Button](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).  
  
-   Using radio buttons to select chart styles. For more information, see [Walkthrough: Updating a Chart in a Document Using Radio Buttons](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).  
  
-  
  
## See Also  
 [Walkthroughs Using Word](../vsto/walkthroughs-using-word.md)   
 [Office Development Samples and Walkthroughs](../vsto/office-development-samples-and-walkthroughs.md)   
 [NamedRange Control](../vsto/namedrange-control.md)   
 [Limitations of Windows Forms Controls on Office Documents](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  