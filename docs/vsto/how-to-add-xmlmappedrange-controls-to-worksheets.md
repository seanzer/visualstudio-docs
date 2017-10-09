---
title: "How to: Add XMLMappedRange Controls to Worksheets | Microsoft Docs"
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
  - "XMLMappedRange control, adding to worksheets"
  - "controls [Office development in Visual Studio], adding to worksheets"
ms.assetid: e1d4f2a8-1157-49c2-9158-a1253b709cb8
caps.latest.revision: 25
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# How to: Add XMLMappedRange Controls to Worksheets
  When you map an XML element to a cell in Microsoft Office Excel, Visual Studio automatically adds an <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control to your worksheet.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  The <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control is not available on the **Toolbox** or the **Data Sources** window. Additionally, you cannot create <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controls programmatically.  
  
### To add an XMLMappedRange control to a worksheet  
  
1.  Open the Excel workbook in the Visual Studio designer.  
  
2.  Open the worksheet where you want to add the control.  
  
3.  On the **Developer** tab, click **Source**.  
  
    > [!NOTE]  
    >  If the **Developer** tab is not visible on the Ribbon, you must enable it. For more information, see [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
     The **XML Source** task pane appears.  
  
4.  In the **XML Source** task pane, click **XML Maps**.  
  
5.  In the **XML Maps** dialog box, click **Add**.  
  
     The **XML Source** dialog box appears.  
  
6.  Select an XML schema from the **XML Source** dialog box and click **Open**.  
  
     The schema is added to the **XML Maps** dialog box.  
  
7.  In the **XML Maps** dialog box, click **OK**.  
  
8.  Drag an element from the **XML Source** task pane to a cell on the worksheet.  
  
     An <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> is created and added to the project.  
  
    > [!NOTE]  
    >  If you drag a parent element from the **XML Source** task pane, a <xref:Microsoft.Office.Tools.Excel.ListObject> control is created.  
  
## See Also  
 [XmlMappedRange Control](../vsto/xmlmappedrange-control.md)   
 [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [How to: Map Schemas to Worksheets Inside Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  