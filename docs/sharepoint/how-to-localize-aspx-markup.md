---
title: "How to: Localize ASPX Markup | Microsoft Docs"
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
  - "localizing XML [SharePoint development in Visual Studio]"
  - "SharePoint development in Visual Studio, localizing"
ms.assetid: 9559a1d1-6558-4c24-a51e-c6ee79432778
caps.latest.revision: 16
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# How to: Localize ASPX Markup
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] (.aspx) pages typically use hard-coded string values. To localize these strings, replace them with expressions that reference localized resources.  
  
## Localizing ASPX Markup  
  
#### To localize ASPX markup  
  
1.  Add separate resource files: one for the default language and one for each localized language.  
  
     If you are localizing only markup and not code, add a Global Resources File project item. If you are localizing code and markup, add a Resources File project item.  
  
    1.  To add a Global Resources File, in **Solution Explorer**, open the shortcut menu for a SharePoint project item, and then choose **Add**, **New Item**. Under the SharePoint **2010** node, choose the **Global Resources File** template.  
  
    2.  To add a Resources File, in **Solution Explorer**, open the shortcut menu for a SharePoint project item, and then choose **Add**, **New Item**. Under either the **Visual Basic** or **Visual C#** node, choose the **Resources File** template.  
  
    > [!NOTE]  
    >  Be sure to add the resource files to a SharePoint project item to enable the Deployment Type property. This property is required later in this procedure. If your solution does not have a SharePoint project item, you can add an Empty SharePoint Project and remove its default Elements.xml file.  
  
2.  Give the default language resource file a name of your choice appended with a .resx extension, such as MyAppResources.resx. Use the same base name for each localized resource file, but add the culture [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. For example, name a German localized resource MyAppResources.de-DE.resx.  
  
3.  Change the value of the **Deployment Type** property of each resource file to **AppGlobalResource** to cause them to deploy to the server's App_GlobalResources folder.  
  
4.  If you are using the resources to localize code in addition to ASPX markup, leave the value of the **Build Action** property of each file as **Embedded Resource**. If you are using the resource files only to localize markup, you can optionally change the property value of the files to **Content**. For more information, see [Localizing SharePoint Solutions](../sharepoint/localizing-sharepoint-solutions.md).  
  
5.  Open each resource file and add localized strings, using the same string IDs in each file.  
  
6.  In the [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] markup for the ASPX page or control, replace the hard-coded strings with values that use the following format:  
  
    ```  
    <%$Resources:Resource File Name, String ID%>  
    ```  
  
     For example, to localize the text for a label control on an application page, you would change:  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>  
    </asp:Content>  
    ```  
  
     to  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>  
    </asp:Content>  
    ```  
  
7.  Choose the F5 key to build and run the application.  
  
8.  In SharePoint, change the display language from the default.  
  
     The localized strings appear in the application. To display localized resources, the SharePoint server must have a language pack installed that matches the resource file's culture.  
  
## See Also  
 [Localizing SharePoint Solutions](../sharepoint/localizing-sharepoint-solutions.md)   
 [How to: Localize a Feature](../sharepoint/how-to-localize-a-feature.md)   
 [How to: Add a Resource File](../sharepoint/how-to-add-a-resource-file.md)   
 [How to: Localize Code](../sharepoint/how-to-localize-code.md)  
  
  