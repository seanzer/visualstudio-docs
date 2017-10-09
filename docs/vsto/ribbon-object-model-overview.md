---
title: "Ribbon Object Model Overview | Microsoft Docs"
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
  - "Ribbon [Office development in Visual Studio], object model"
ms.assetid: cae24f66-e980-41ee-a915-d4c8e03efbc1
caps.latest.revision: 75
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# Ribbon Object Model Overview
  The [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] exposes a strongly typed object model that you can use to get and set the properties of ribbon controls at run time. For example, you can dynamically populate menu controls, or show and hide controls contextually. You can also add tabs, groups, and controls to a ribbon, but only before the ribbon is loaded by the Office application. For information, see [Setting Properties That Become Read-Only](#SettingReadOnlyProperties).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 This Ribbon object model consists mainly of the [Ribbon Class](#RibbonClass), [Ribbon Events](#RibbonEvents), and [Ribbon Control Classes](#RibbonControlClasses).  
  
##  <a name="RibbonClass"></a> Ribbon Class  
 When you add a new **Ribbon (Visual Designer)** item to a project, Visual Studio adds a **Ribbon** class to your project. The **Ribbon** class inherits from the <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> class.  
  
 This class appears as a partial class that is split between the Ribbon code file and the Ribbon Designer code file.  
  
##  <a name="RibbonEvents"></a> Ribbon Events  
 The **Ribbon** class contains the following three events:  
  
|Event|Description|  
|-----------|-----------------|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Raised when the Office application loads the ribbon customization. The <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load> event handler is automatically added to the ribbon code file. Use this event handler to run custom code when the ribbon loads.|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Enables you to cache images in the ribbon customization when the ribbon loads. You can get a slight performance gain if you write code to cache the ribbon images in this event handler. For more information, see <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Raised when the ribbon instance closes.|  
  
##  <a name="RibbonControlClasses"></a> Ribbon Controls  
 The <xref:Microsoft.Office.Tools.Ribbon> namespace contains a type for each control that you see in the **Office Ribbon Controls** group of the **Toolbox**.  
  
 The following table shows the type for each `Ribbon` control. For a description of each control, see [Ribbon Overview](../vsto/ribbon-overview.md).  
  
|Control name|Class name|  
|------------------|----------------|  
|**Box**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**Button**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|  
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|  
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|  
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|  
|**DropDown**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|  
|**EditBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Gallery**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**Group**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Label**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|  
|**Menu**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Separator**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**Tab**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
  
 The <xref:Microsoft.Office.Tools.Ribbon> namespace uses the "Ribbon" prefix for these types to avoid a name collision with the names of control classes in the <xref:System.Windows.Forms> namespace.  
  
 When you add a control to the Ribbon Designer, the Ribbon Designer declares the class for that control as a field in the Ribbon Designer code file.  
  
### Common Tasks Using the Properties of Ribbon Controls  
 Each `Ribbon` control contains properties that you can use to perform various tasks, such as assigning a label to a control, or hiding and showing controls.  
  
 In some cases, properties become read-only after the ribbon loads or after a control is added to a dynamic menu. For more information, see [Setting Properties that Become Read-Only](#SettingReadOnlyProperties).  
  
 The following table describes some of the tasks that you can perform by using `Ribbon` control properties.  
  
|For this task:|Do this:|  
|--------------------|--------------|  
|Hide or show a control.|Use the Visible property.|  
|Enable or disable a control.|Use the Enabled property.|  
|Set the size of a control.|Use the ControlSize property.|  
|Get the image that appears on a control.|Use the Image property.|  
|Change the label of a control.|Use the Label property.|  
|Add user-defined data to a control.|Use the Tag property.|  
|Get the items in a <xref:Microsoft.Office.Tools.Ribbon.RibbonBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>, or<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> control.|Use the Items property.|  
|Add items to a <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, or <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> control.|Use the Items property.|  
|Add controls to a <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>.|Use the Items property.<br /><br /> To add controls to the <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> after the ribbon is loaded into the Office application, you must set the <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> property to **true** before the ribbon is loaded into the Office application. For information, see [Setting Properties That Become Read-Only](#SettingReadOnlyProperties).|  
|Get the selected item of a <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>,<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, or <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Use the SelectedItem property. For a <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, use the <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A> property.|  
|Get the groups on a <xref:Microsoft.Office.Tools.Ribbon.RibbonTab>.|Use the <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A> property.|  
|Specify the number of rows and columns that appear in a <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Use the <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> and <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> properties.|  
  
##  <a name="SettingReadOnlyProperties"></a> Setting Properties That Become Read-Only  
 Some properties can only be set before the ribbon loads. There are three places to set these properties:  
  
-   In the Visual Studio **Properties** window.  
  
-   In the constructor of the **Ribbon** class.  
  
-   In the CreateRibbonExtensibilityObject method of the `ThisAddin`, `ThisWorkbook`, or `ThisDocument` class of your project.  
  
 Dynamic menus provide some exceptions. You can create new controls, set their properties, and then add them to a dynamic menu at run time, even after the ribbon that contains the menu is loaded.  
  
 Properties of controls that you add to a dynamic menu can be set at any time.  
  
 For more information, see [Properties that Become Read-Only](#ReadOnlyProperties).  
  
### Setting Properties in the Constructor of the Ribbon  
 You can set the properties of a `Ribbon` control in the constructor of the **Ribbon** class. This code must appear after the call to the `InitializeComponent` method. The following example adds a new button to a group if the current time is 17:00 Pacific Time (UTC-8) or later.  
  
 Add the following code.  
  
 [!code-csharp[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/CSharp/trin_ribbon_objectmodel_dotnet4/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/VisualBasic/trin_ribbon_objectmodel_dotnet4/Ribbon1.Designer.vb#1)]  
  
 In Visual C# projects that you upgraded from Visual Studio 2008, the constructor appears in the ribbon code file.  
  
 In Visual Basic projects, or in Visual C# projects that you created in [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], the constructor appears in the Ribbon Designer code file. This file is named *YourRibbonItem*.Designer.cs or *YourRibbonItem*.Designer.vb. To see this file in Visual Basic projects, you must first click the **Show All Files** button in Solution Explorer.  
  
### Setting Properties in the CreateRibbonExtensibilityObject Method  
 You can set the properties of a `Ribbon` control when you override the CreateRibbonExtensibilityObject method in the `ThisAddin`, `ThisWorkbook`, or `ThisDocument` class of your project. For more information about the CreateRibbonExtensibilityObject method, see [Ribbon Overview](../vsto/ribbon-overview.md).  
  
 The following example sets ribbon properties in the CreateRibbonExtensibilityObject method of the `ThisWorkbook` class of an Excel workbook project.  
  
 Add the following code.  
  
 [!code-vb[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/VisualBasic/trin_ribbon_objectmodel_dotnet4/ThisWorkbook.vb#2)]
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/CSharp/trin_ribbon_objectmodel_dotnet4/ThisWorkbook.cs#2)]  
  
###  <a name="ReadOnlyProperties"></a> Properties That Become Read-Only  
 The following table shows properties that can only be set before the Ribbon loads.  
  
> [!NOTE]  
>  You can set the properties of controls on dynamic menus at any time. This table does not apply in that case.  
  
|Property|Ribbon control class|  
|--------------|--------------------------|  
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**ColumnCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Dynamic**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Global**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Groups**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**MaxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Name**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|  
|**Position**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**RowCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Tabs**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Title**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
  
### Setting Properties for Ribbons that Appear in Outlook Inspectors  
 A new instance of the ribbon is created each time a user opens an Inspector in which the ribbon appears. However, you can set the properties listed in the table above only before the first instance of the ribbon is created. After the first instance is created, these properties become read-only because the first instance defines the XML file that Outlook uses to load the ribbon.  
  
 If you have conditional logic that sets any of these properties to a different value when other instances of the ribbon are created, this code will have no effect.  
  
> [!NOTE]  
>  Ensure that the **Name** property is set for each control that you add to an Outlook ribbon. If you add a control to an Outlook ribbon at run time, you must set this property in your code. If you add a control to an Outlook ribbon at design time, the Name property is set automatically.  
  
## Ribbon Control Events  
 Each control class contains one or more events. The following table describes these events.  
  
|Event|Description|  
|-----------|-----------------|  
|Click|Occurs when a control is clicked.|  
|TextChanged|Occurs when the text of an edit box or combo box is changed.|  
|ItemsLoading|Occurs when the Items collection of the control is requested by Office. Office caches the Items collection until your code changes the properties of the control, or you call the <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> method.|  
|ButtonClick|Occurs when a button in a <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> or <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> is clicked.|  
|SelectionChanged|Occurs when the selection in a <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> or <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> changes.|  
|DialogLauncherClick|Occurs when the dialog launcher icon in the lower-right corner of a group is clicked.|  
  
 The event handlers for these events have the following two parameters.  
  
|Parameter|Description|  
|---------------|-----------------|  
|*sender*|An <xref:System.Object> that represents the control that raised the event.|  
|*e*|A <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs> that contains a <xref:Microsoft.Office.Core.IRibbonControl>. Use this control to access any property that is not available in the Ribbon object model provided by the [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|  
  
## See Also  
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Ribbon Overview](../vsto/ribbon-overview.md)   
 [How to: Get Started Customizing the Ribbon](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Ribbon Designer](../vsto/ribbon-designer.md)   
 [Walkthrough: Creating a Custom Tab by Using the Ribbon Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Walkthrough: Updating the Controls on a Ribbon at Run Time](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Customizing a Ribbon for Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [How to: Customize a Built-in Tab](../vsto/how-to-customize-a-built-in-tab.md)   
 [How to: Add Controls to the Backstage View](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [How to: Export a Ribbon from the Ribbon Designer to Ribbon XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [How to: Show Add-in User Interface Errors](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  