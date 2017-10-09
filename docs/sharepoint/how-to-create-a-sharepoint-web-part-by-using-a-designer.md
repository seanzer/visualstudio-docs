---
title: "How to: Create a SharePoint Web Part by Using a Designer | Microsoft Docs"
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
  - "Web Parts [SharePoint development in Visual Studio], designer"
  - "Web Parts [SharePoint development in Visual Studio], adding"
  - "Web Parts [SharePoint development in Visual Studio], creating"
ms.assetid: 6b88f3ef-02ff-4135-80ff-b4acacf8c695
caps.latest.revision: 26
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# How to: Create a SharePoint Web Part by Using a Designer
  You can create a web part by adding a **Visual Web Part** item to any SharePoint project. This opens the Visual Web Developer designer in Visual Studio where you can add controls and code to the web part. Visual web parts function the same way as web parts do. The only difference is that you design visual web parts in the Visual Web Developer designer.  
  
### To create a project for visual web parts  
  
1.  On the menu bar, choose **File**, **New**, **Project**.  
  
     The **New Project** dialog box opens.  
  
2.  In the **New Project** dialog box, under either **Visual C#** or **Visual Basic**, expand the **Office/SharePoint** node, and then choose the **SharePoint Solutions** category.  
  
3.  In the list of project templates, choose **SharePoint 2013 - Visual Web Part**, and then choose the **OK** button.  
  
     The **SharePoint Customization Wizard** appears.  
  
4.  On the **Specify the site and security level for debugging** page, specify the URL of a SharePoint site that's on the local computer, and then choose the **Finish** button.  
  
     In **Solution Explorer**, a web part appears. After designing the web part in the Visual Web Developer designer, you'll test it on the site that you specify.  
  
### To add a visual web part to an existing SharePoint project  
  
1.  On the menu bar, choose **Project**, **Add New Item**.  
  
2.  In the **Add New Item** dialog box, choose the **Office/SharePoint** node.  
  
3.  In the list of project templates, choose **Visual Web Part**, name it, and then choose the **Add** button.  
  
     In **Solution Explorer**, your web part appears. After designing the web part in the Visual Web Developer designer, you'll test it on the site that you specify.  
  
## See Also  
 [Creating Web Parts for SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [How to: Create a SharePoint Web Part](../sharepoint/how-to-create-a-sharepoint-web-part.md)   
 [Walkthrough: Creating a Web Part for SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [Walkthrough: Creating a Web Part for SharePoint by Using a Designer](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  