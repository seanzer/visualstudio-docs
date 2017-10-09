---
title: "How to: Customize a SharePoint Feature | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.RAD.FeatureDesigner.SwitchView"
  - "VS.SharePointTools.RAD.featureDesigner.Manifest"
  - "VS.SharePointTools.RAD.FeatureDesignerProperties"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint development in Visual Studio, features"
ms.assetid: e624c546-564b-4c73-9f1b-dc3675e76a55
caps.latest.revision: 23
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# How to: Customize a SharePoint Feature
  You can create and customize SharePoint features by using the Feature Designer in Visual Studio. For example, you can set the Feature scope and add other Features as dependencies. By default, the Feature Designer is opened when you add a new Feature in Solution Explorer or the SharePoint Package Explorer.  
  
## Opening the Feature Designer  
 You can add or remove SharePoint project items to a Feature using the Feature Designer.  
  
#### To open the Feature Designer  
  
1.  In **Solution Explorer**, expand **Features**.  
  
2.  Double-click the *Feature1* item, or open the shortcut menu for the *Feature1* item and then choose **View Designer**.  
  
## Viewing the Packaged Manifest File  
 You can use the Feature Designer to modify and generate the packaged manifest file for the Feature (feature.xml). Then, you can view the XML code for this file in Visual Studio.  
  
#### To view the packaged manifest file  
  
1.  In the **Feature Designer**, choose the **Manifest** tab.  
  
#### To view the packaged manifest file by using Solution Explorer  
  
1.  In **Solution Explorer**, choose the **Show All Files** icon.  
  
2.  Expand Features, expand FeatureName, expand FeatureName.feature, and then open the *FeatureName*.Template.xml file.  
  
    > [!NOTE]  
    >  When you open the Feature template manifest XML file, the files are automatically validated and the warnings that appear in the Error List window can be ignored.  
  
## Changing the Manifest Template  
 You can change the XML code for the Feature manifest file in the Visual Studio XML Editor or the Manifest Template pane. Any changes to the XML code is merged into the packaged manifest file for the Feature. For example, you may want to change the manifest template to customize a Feature property.  
  
#### To change the manifest template by using the XML Editor  
  
1.  In the **Feature Designer**, choose the **Manifest** tab, expand the **Edit Options** node, and then choose the **Open in XML Editor** link.  
  
     Changes to the XML are merged into the packaged manifest file.  
  
#### To change the manifest template by using the Manifest Template pane  
  
1.  In the **Feature Designer**, choose the **Manifest** tab, expand the **Edit Options** node, and then change the XML that appears in the Manifest Template pane.  
  
     Changes to the XML appear in the **Preview of Packaged Manifest** pane.  
  
## Overwriting the Packaged Manifest File  
 You can disable the Feature Designer and create the feature.xml file manually. The first time that you perform this procedure, the current settings in the Feature Designer are saved to the Feature template XML file. Then, you can modify or overwrite the XML code.  
  
> [!NOTE]  
>  If you add or remove SharePoint project items in the XML file while the Feature Designer is disabled, these project items are not packaged.  
  
#### To overwrite packaged manifest file by disabling the designer  
  
1.  In the **Feature Designer**, choose the **Manifest** tab.  
  
2.  Expand the **Edit Options** node, choose the **Overwrite generated XML and edit manifest in the XML editor** link, and then choose the **Yes** button.  
  
     The template is updated with the current packaged manifest file.  
  
## Enabling the Feature Designer  
 You can re-enable the Feature Designer to customize the feature.xml file.  
  
#### To re-enable the designer  
  
1.  In the **Feature Designer**, choose the **Discard manifest edits and re-enable the designer** link, and then choose the **Yes** button.  
  
2.  The template is refreshed with the original text, and any changes to the XML are lost.  
  
## See Also  
 [Packaging and Deploying SharePoint Solutions](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  