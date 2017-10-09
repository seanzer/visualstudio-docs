---
title: "Using Local Database Files in Office Solutions Overview | Microsoft Docs"
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
  - "Office applications [Office development in Visual Studio], data"
  - "data [Office development in Visual Studio], local"
  - "local data [Office development in Visual Studio]"
ms.assetid: 7a920e6b-f0c3-4a62-b5dd-02668a6177b6
caps.latest.revision: 30
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# Using Local Database Files in Office Solutions Overview
  You can include a database file, such as a SQL Server Express (.mdf) file or a Microsoft Office Access (.mdb) file, in your Office solution. This enables end users to maintain a local database in situations where maintaining a centralized database is not required, for example in a local inventory solution that is used on only a single computer.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Importing the Database File into a Project  
 To import the database file into your project, use the **Data Source Configuration Wizard** to create a data source based on the database file. The wizard adds the database file and a typed dataset to your project.  
  
## Deploying the Database File  
 The **Data Source Configuration Wizard** uses a relative path to create connections to the local database file. This enables you to copy the solution from one computer to another if you maintain the relative positions of the files.  
  
 If you deploy your solution to a server and then distribute the document to each end user, you must also manually distribute the database file and install it in the same position relative to the document. This means that the end user cannot move the document to a new location on his or her computer, unless he or she also moves the database file.  
  
## Local Database Files and Caching the Dataset  
 In document-level solutions for Microsoft Office Excel and Microsoft Office Word, you can cache datasets in the document by marking the dataset instance with the attribute <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>. When you add the database file to your project by using the **Data Source Configuration Wizard**, a typed dataset is added to your project automatically. It is rarely necessary to apply <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> to this dataset, because the data is already local on the user's computer. For more information, see [Caching Data](../vsto/caching-data.md).  
  
## See Also  
 [Binding Data to Controls in Office Solutions](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [How to: Populate Documents with Data from a Database](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [How to: Update a Data Source with Data from a Host Control](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Deploying an Office Solution](../vsto/deploying-an-office-solution.md)   
 [Caching Data](../vsto/caching-data.md)  
  
  