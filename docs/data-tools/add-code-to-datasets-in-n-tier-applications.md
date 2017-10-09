---
title: "Add code to datasets in n-tier applications | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "n-tier applications, extending datasets"
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: 20
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
translation.priority.ht: 
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "ru-ru"
  - "zh-cn"
  - "zh-tw"
translation.priority.mt: 
  - "cs-cz"
  - "pl-pl"
  - "pt-br"
  - "tr-tr"
ms.technology: "vs-data-tools"
---
# Add code to datasets in n-tier applications
You can extend the functionality of a dataset by creating a partial class file for the dataset and adding code to it (instead of adding code to the *DatasetName*.Dataset.Designer file). Partial classes enable code for a specific class to be divided among multiple physical files. For more information, see [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) or [Partial Classes and Methods](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).  
  
 The code that defines a dataset is generated every time changes are made to the dataset definition (in the typed dataset). This code is also generated when you make changes during the running of any wizard that modifies the configuration of a dataset. To prevent your code from being deleted during the regeneration of a dataset, add code to the dataset's partial class file.  
  
 By default, after you separate the dataset and TableAdapter code, the result is a discrete class file in each project. The original project has a file named *DatasetName*.Designer.vb (or *DatasetName*.Designer.cs) that contains the TableAdapter code. The project that's designated in the **Dataset Project** property has a file that's named *DatasetName*.DataSet.Designer.vb (or *DatasetName*.DataSet.Designer.cs).This file contains the dataset code.  
  
> [!NOTE]
>  When you separate datasets and TableAdapters (by setting the **DataSet Project** property), existing partial dataset classes in the project won't be moved automatically. Existing dataset partial classes must be moved manually to the dataset project.  
  
> [!NOTE]
>  When validation code needs to be added, the typed dataset provides functionality for generating <xref:System.Data.DataTable.ColumnChanging> and <xref:System.Data.DataTable.RowChanging> event handlers. For more information, see [Add validation to an n-tier dataset](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
### To add code to datasets in n-tier applications  
  
1.  Locate the project that contains the .xsd file. 
  
2.  Select the **.xsd** file to open the dataset.  
  
3.  Right-click the data table to which you want to add code (the table name in the title bar), and then select **View Code**.  
  
     A partial class is created and opens in the Code Editor.  
  
4.  Add code inside the partial class declaration.  
  
     The following example shows where to add code to the CustomersDataTable in the NorthwindDataSet:  
  
    ```vb  
    Partial Public Class CustomersDataTable  
        ' Add code here to add functionality   
        ' to the CustomersDataTable.  
    End Class  
    ```    
    ```csharp  
    partial class CustomersDataTable  
    {  
        // Add code here to add functionality  
        // to the CustomersDataTable.  
    }  
    ```  
  
## See Also  
 [N-Tier Data Applications Overview](../data-tools/n-tier-data-applications-overview.md)   
 [Add code to TableAdapters in n-tier applications](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)   
 [Create and Configure TableAdapters](create-and-configure-tableadapters.md)   
 [Create and Configure TableAdapters](create-and-configure-tableadapters.md)   
 [Hierarchical Update Overview](hierarchical-update.md)     
 [Dataset tools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)