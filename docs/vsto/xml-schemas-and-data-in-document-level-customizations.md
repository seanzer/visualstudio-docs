---
title: "XML Schemas and Data in Document-Level Customizations | Microsoft Docs"
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
  - "XML schemas [Office development in Visual Studio]"
  - "schemas [Office development in Visual Studio]"
  - "XML [Office development in Visual Studio], XML schemas"
  - "XML schemas [Office development in Visual Studio], about XML schemas and data"
  - "Office development in Visual Studio, XML"
ms.assetid: 74bd5773-6cb0-44fb-9738-75e2f2c6e48d
caps.latest.revision: 28
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# XML Schemas and Data in Document-Level Customizations
  **Important** The information set out in this topic regarding Microsoft Word is presented exclusively for the benefit and use of individuals and organizations who are located outside the United States and its territories or who are using, or developing programs that run on, Microsoft Word products that were licensed by Microsoft before January 2010, when Microsoft removed an implementation of particular functionality related to custom XML from Microsoft Word. This information regarding Microsoft Word may not be read or used by individuals or organizations in the United States or its territories who are using, or developing programs that run on, Microsoft Word products that were licensed by Microsoft after January 10, 2010; those products will not behave the same as products licensed before that date or purchased and licensed for use outside the United States.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Microsoft Office Excel and Microsoft Office Word provide the capability to map schemas to your documents. This feature can simplify importing and exporting XML data in and out of the document.  
  
 Visual Studio exposes mapped schema elements in document-level customizations as controls in the programming model. For Excel, Visual Studio adds support for binding the controls to data in databases, Web services, and objects. For Word and Excel, Visual Studio adds support for actions panes, which can be used with a schema-mapped document to create an enhanced end user experience for your solutions. For more information, see [Actions Pane Overview](../vsto/actions-pane-overview.md).  
  
> [!NOTE]  
>  You cannot use multipart XML schemas in Excel solutions.  
  
## Objects Created when Schemas are Attached to Excel Workbooks  
 When you attach a schema to a workbook, Visual Studio automatically creates several objects and adds them to your project. These objects should not be deleted using Visual Studio tools, because they are managed by Excel. To delete them, remove the mapped elements from the worksheet or detach the schema by using Excel tools.  
  
 There are two main objects:  
  
-   XML schema (XSD file). For every schema in the workbook, Visual Studio adds a schema to the project. This appears as a project item with an XSD extension in **Solution Explorer**.  
  
-   A typed <xref:System.Data.DataSet> class. This class is created based on the schema. This dataset class is visible in **Class View**.  
  
## Objects Created when Schema Elements are Mapped to Excel Worksheets  
 When you map a schema element from the **XML Source** task pane to a worksheet, Visual Studio automatically creates several objects and adds them to your project:  
  
-   Controls. For every mapped object in the workbook, an <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control (for non-repeating schema elements) or a <xref:Microsoft.Office.Tools.Excel.ListObject> control (for repeating schema elements) is created in the programming model. The <xref:Microsoft.Office.Tools.Excel.ListObject> control can be deleted only by deleting the mappings and the mapped objects from the workbook. For more information about controls, see [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
-   BindingSource. When you create an <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> by mapping a non-repeating schema element to the worksheet, a <xref:System.Windows.Forms.BindingSource> is created and the <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control is bound to the <xref:System.Windows.Forms.BindingSource>. You must bind the <xref:System.Windows.Forms.BindingSource> to an instance of the data source that matches the schema mapped to the document, such as an instance of the typed <xref:System.Data.DataSet> class that was created. Create the binding by setting the <xref:System.Windows.Forms.BindingSource.DataSource%2A> and <xref:System.Windows.Forms.BindingSource.DataMember%2A> properties, which are exposed in the **Properties** window.  
  
    > [!NOTE]  
    >  The <xref:System.Windows.Forms.BindingSource> is not created for <xref:Microsoft.Office.Tools.Excel.ListObject> objects. You must manually bind the <xref:Microsoft.Office.Tools.Excel.ListObject> to the data source by setting the <xref:System.Windows.Forms.BindingSource.DataSource%2A> and <xref:System.Windows.Forms.BindingSource.DataMember%2A> properties in the **Properties** window.  
  
### Office Mapped Schemas and the Visual Studio Data Sources Window  
 Both the mapped schema functionality of Office and the Visual Studio **Data Sources** window can help you present data on an Excel worksheet for reporting or editing. In both cases you can drag data elements onto the Excel worksheet. Both methods create controls that are data bound through a <xref:System.Windows.Forms.BindingSource> to a data source such as a <xref:System.Data.DataSet> or a Web service.  
  
> [!NOTE]  
>  When you map a repeating schema element to a worksheet, Visual Studio creates a <xref:Microsoft.Office.Tools.Excel.ListObject>. The <xref:Microsoft.Office.Tools.Excel.ListObject> is not automatically bound to data through the <xref:System.Windows.Forms.BindingSource>. You must manually bind the <xref:Microsoft.Office.Tools.Excel.ListObject> to the data source by setting the <xref:System.Windows.Forms.BindingSource.DataSource%2A> and <xref:System.Windows.Forms.BindingSource.DataMember%2A> properties in the **Properties** window.  
  
 The following table shows some of the differences between the two methods.  
  
|XML schema|Data Sources window|  
|----------------|-------------------------|  
|Uses Office interface.|Uses **Data Sources** window in Visual Studio.|  
|Enables the built-in Office features for importing and exporting data from XML files.|You must provide import and export functionality programmatically.|  
|You must write code to fill the generated controls with data.|Controls added from the **Data Sources** window have code generated automatically to fill them, along with the necessary connection strings when you use database servers.|  
  
## Behavior when Schemas are Attached to Word Documents  
 Data objects are not created when you attach a schema to a Word document that is used in a document-level Office project. However, when you map a schema element to your document, controls are created. The type of control depends on what type of element you map; repeating elements generate <xref:Microsoft.Office.Tools.Word.XMLNodes> controls, and non-repeating elements generate <xref:Microsoft.Office.Tools.Word.XMLNode> controls. For more information, see [XMLNodes Control](../vsto/xmlnodes-control.md) and [XMLNode Control](../vsto/xmlnode-control.md).  
  
## Deployment of Solutions That Include XML Schemas  
 You should create an installer to deploy a solution that uses an XML schema that is mapped to a document. The installer should register the schema in the schema library on the user's computer. If you do not register the schema, the solution will still work because Word generates a temporary schema based on the elements that are in the document when the user opens it. However, the user will not be able to perform validation against or save the schema that was used to create the project. For more information about installers, see [Deploying Applications, Services, and Components](/visualstudio/deployment/deploying-applications-services-and-components).  
  
 You can also add code to your project to check whether the schema is in the library and registered. If it is not, you can warn the user.  
  
 [!code-vb[Trin_VstcoreDataWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstcoreDataWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs#1)]  
  
## See Also  
 [How to: Map Schemas to Word Documents Inside Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [How to: Map Schemas to Worksheets Inside Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  