---
title: "How to: Show the Developer Tab on the Ribbon | Microsoft Docs"
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
  - "Ribbon [Office development in Visual Studio], tabs"
  - "Developer tab [Office development in Visual Studio]"
ms.assetid: ce7cb641-44f2-4a40-867e-a7d88f8e98a9
caps.latest.revision: 35
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# How to: Show the Developer Tab on the Ribbon
  To access the **Developer** tab on the ribbon of an Office application, you must configure it to show that tab because it doesn't appear by default. For example, you must show that tab if you want to add a <xref:Microsoft.Office.Tools.Word.GroupContentControl> to a document-level customization for Word.  
  
> [!NOTE]  
>  This guidance applies to Office 2010 or later applications only. If you want to show this tab in the 2007 Microsoft Office System, see the following version of this topic [How to: Show the Developer Tab on the Ribbon](http://msdn.microsoft.com/library/bb608625(v=vs.90).aspx).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  Access doesn't have a **Developer** tab.  
  
### To show the Developer tab  
  
1.  Start any of the Office applications supported by this topic. See the **Applies to:** note earlier in this topic.  
  
2.  On the **File** tab, choose the **Options** button.  
  
     The following figure shows the **File** tab and **Options** button in Office 2010.  
  
     ![Choosing File, Options in Outlook 2010](../vsto/media/vsto-office-file-tab.png "Choosing File, Options in Outlook 2010")  
  
     The following figure shows the **File** tab in Office 2013.  
  
     ![The File tab in Outlook 2013](../vsto/media/vsto-office2013-filetab.png "The File tab in Outlook 2013")  
  
     The following figure shows the **Options** button in Office 2013.  
  
     ![The Options button in Outlook 2013 Preview](../vsto/media/vsto-office2013-optionsbutton.png "The Options button in Outlook 2013 Preview")  
  
3.  In the *ApplicationName***Options** dialog box, choose the **Customize Ribbon** button.  
  
     The following figure shows the **Options** dialog box and the **Customize Ribbon** button in Excel 2010. The location of this button is similar in all other applications listed in the "Applies to" section near the top of this topic.  
  
     ![The Customize Ribbon button](../vsto/media/vsto-office2010-customizeribbonbutton.png "The Customize Ribbon button")  
  
4.  In the list of main tabs, select the **Developer** check box.  
  
     The following figure shows the **Developer** check box in Word 2010 and [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]. The location of this check box is similar in all other applications listed in the "Applies to" section near the top of this topic.  
  
     ![The Developer check box in the Word Options dialog](../vsto/media/vsto-office2010-developercheckbox.png "The Developer check box in the Word Options dialog")  
  
5.  Choose the **OK** button to close the **Options** dialog box.  
  
## See Also  
 [Office UI Customization](../vsto/office-ui-customization.md)  
  
  