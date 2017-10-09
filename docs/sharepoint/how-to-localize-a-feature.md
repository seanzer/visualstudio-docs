---
title: "How to: Localize a Feature | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "features [SharePoint development in Visual Studio]"
  - "SharePoint development in Visual Studio, localizing"
ms.assetid: 66a0b389-1f71-421f-9817-a19840765d83
caps.latest.revision: 17
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# How to: Localize a Feature
  By default, feature titles and descriptions use hard-coded string values. To localize the feature title and description, replace the strings with expressions that reference localized resources.  
  
## Localizing a Feature  
  
#### To localize a feature  
  
1.  In **Solution Explorer**, open the shortcut menu for the **Feature1** node, and then choose **Add Feature Resource**.  
  
2.  In the **Add Resource** dialog box, choose **Invariant Language** from the list as the culture for the default language feature resource file.  
  
3.  Repeat the previous step for each localized language, choosing the languages of your choice for the localized feature resource files.  
  
     Separate feature resource files are created: one for the default language and one for each localized language that you want to support.  
  
4.  Open each resource file in the Resource Editor, and then enter all of the string IDs and their values.  
  
     For example, in the default feature resource file, enter a string ID of **Title** with a value of **My Feature Title**, and a second string ID of **Description** with a value of **My Feature Description**. For each localized resource file, use the same string IDs used in the default feature resource, but enter localized strings for the values.  
  
5.  After you enter all the resource values, open the shortcut menu for the feature (for instance, Feature1.feature), and then choose **View Designer** to open the feature in the Feature Designer.  
  
6.  To localize the **Title** and **Description** fields in the feature, use the following format to enter values in their boxes:  
  
     `$Resources:` *String ID*  
  
     For example, enter $Resources:**Title** in the **Feature Title** box, and $Resources:**Description** in the **Feature Description** box.  
  
     The string IDs must match those that are used in the resource files.  
  
7.  Choose the F5 key to build and run the application.  
  
8.  In SharePoint, open the **Site Actions** menu, choose **Site Settings**, and then, in the **Site Actions** section choose the **Manage Site Features** link.  
  
9. In SharePoint, change the display language from the default.  
  
     The localized feature title and description appear in the application. To display localized resources, the SharePoint server must have a language pack installed that matches the resource file's culture.  
  
## See Also  
 [Localizing SharePoint Solutions](../sharepoint/localizing-sharepoint-solutions.md)   
 [How to: Add a Resource File](../sharepoint/how-to-add-a-resource-file.md)   
 [How to: Localize ASPX Markup](../sharepoint/how-to-localize-aspx-markup.md)   
 [How to: Localize Code](../sharepoint/how-to-localize-code.md)  
  
  