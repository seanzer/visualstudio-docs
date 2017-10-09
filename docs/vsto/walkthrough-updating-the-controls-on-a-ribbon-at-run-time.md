---
title: "Walkthrough: Updating the Controls on a Ribbon at Run Time | Microsoft Docs"
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
  - "controls [Office development in Visual Studio], Ribbon"
  - "Ribbon [Office development in Visual Studio], controls"
  - "updating Ribbon controls"
  - "Ribbon [Office development in Visual Studio], dynamic menu"
  - "dynamic menus [Office development in Visual Studio]"
  - "Ribbon [Office development in Visual Studio], updating"
ms.assetid: ed80790f-3f95-47e4-8a41-872588a8ca07
caps.latest.revision: 51
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# Walkthrough: Updating the Controls on a Ribbon at Run Time
  This walkthrough demonstrates how to use the Ribbon object model to update the controls on a Ribbon after the Ribbon is loaded into the Office application.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 The example pulls data from the Northwind sample database to populate a combo box and menu in Microsoft Office Outlook. Items that you select in these controls automatically populate fields such as **To** and **Subject** in an e-mail message.  
  
 This walkthrough illustrates the following tasks:  
  
-   Creating a new Outlook VSTO Add-in project.  
  
-   Designing a custom Ribbon group.  
  
-   Adding the custom group to a built-in tab.  
  
-   Updating controls on the Ribbon at run time.  
  
> [!NOTE]  
>  Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions. The Visual Studio edition that you have and the settings that you use determine these elements. For more information, see [Personalize the Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## Prerequisites  
 You need the following components to complete this walkthrough:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Outlook  
  
## Creating a New Outlook VSTO Add-in Project  
 First, create an Outlook VSTO Add-in project.  
  
#### To create a new Outlook VSTO Add-in project  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], create an Outlook VSTO Add-in project with the name **Ribbon_Update_At_Runtime**.  
  
2.  In the **New Project** dialog box, select **Create directory for solution**.  
  
3.  Save the project to the default project directory.  
  
     For more information, see [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## Designing a Custom Ribbon Group  
 The Ribbon for this example will appear when a user composes a new mail message. To create a custom group for the Ribbon, first add a Ribbon item to your project, and then design the group in the Ribbon Designer. This custom group will help you generate follow-up e-mail messages to customers by pulling names and order histories from a database.  
  
#### To design a custom group  
  
1.  On the **Project** menu, click **Add New Item**.  
  
2.  In the **Add New Item** dialog box, select **Ribbon (Visual Designer)**.  
  
3.  Change the name of the new Ribbon to **CustomerRibbon**, and then click **Add**.  
  
     The **CustomerRibbon.cs** or **CustomerRibbon.vb** file opens in the Ribbon Designer and displays a default tab and group.  
  
4.  Click the Ribbon Designer to select it.  
  
5.  In the **Properties** window, click the drop-down arrow next to the **RibbonType** property, and then click **Microsoft.Outlook.Mail.Compose**.  
  
     This enables the Ribbon to appear when the user composes a new mail message in Outlook.  
  
6.  In the Ribbon Designer, click **Group1** to select it.  
  
7.  In the **Properties** window, set **Label** to **Customer Purchases**.  
  
8.  From the **Office Ribbon Controls** tab of the **Toolbox**, drag a **ComboBox** onto the **Customer Purchases** group.  
  
9. Click **ComboBox1** to select it.  
  
10. In the **Properties** window, set **Label** to **Customers**.  
  
11. From the **Office Ribbon Controls** tab of the **Toolbox**, drag a **Menu** onto the **Customer Purchases** group.  
  
12. In the **Properties** window, set **Label** to **Product Purchased**.  
  
13. Set **Dynamic** to **true**.  
  
     This enables you to add and remove controls on the menu at run time after the Ribbon is loaded into the Office application.  
  
## Adding the Custom Group to a Built-in Tab  
 A built-in tab is a tab that is already on the Ribbon of an Outlook Explorer or Inspector. In this procedure, you will add the custom group to a built-in tab, and then specify the position of the custom group on the tab.  
  
#### To add the custom group to a built-in tab  
  
1.  Click the **TabAddins (Built-In)** tab to select it.  
  
2.  In the **Properties** window, expand the **ControlId** property, and then set **OfficeId** to **TabNewMailMessage**.  
  
     This adds the **Customer Purchases** group to the **Messages** tab of the Ribbon that appears in a new mail message.  
  
3.  Click the **Customer Purchases** group to select it.  
  
4.  In the **Properties** window, expand the **Position** property, click the drop-down arrow next to the **PositionType** property, and then click **BeforeOfficeId**.  
  
5.  Set the **OfficeId** property to **GroupClipboard**.  
  
     This positions the **Customer Purchases** group before the **Clipboard** group of the **Messages** tab.  
  
## Creating the Data Source  
 Use the **Data Sources** window to add a typed dataset to your project.  
  
#### To create the data source  
  
1.  On the **Data** menu, click **Add New Data Source**.  
  
     This starts the **Data Source Configuration Wizard**.  
  
2.  Select **Database**, and then click **Next**.  
  
3.  Select **Dataset**, and then click **Next**.  
  
4.  Select a data connection to the Northwind sample Microsoft SQL Server Compact 4.0 database, or add a new connection by using the **New Connection** button.  
  
5.  After a connection has been selected or created, click **Next**.  
  
6.  Click **Next** to save the connection string.  
  
7.  On the **Choose Your Database Objects** page, expand **Tables**.  
  
8.  Select the check box next to each of the following tables:  
  
    1.  **Customers**  
  
    2.  **Order Details**  
  
    3.  **Orders**  
  
    4.  **Products**  
  
9. Click **Finish**.  
  
## Updating Controls in the Custom Group at Run Time  
 Use the Ribbon object model to perform the following tasks:  
  
-   Add customer names to the **Customers** combo box.  
  
-   Add menu and button controls to the **Products Purchased** menu that represent sales orders and products sold.  
  
-   Populate the To, Subject, and Body fields of new mail messages by using data from the **Customers** combo box and **Products Purchased** menu.  
  
#### To update controls in the custom group by using the Ribbon object model  
  
1.  On the **Project** menu, click **Add Reference**.  
  
2.  In the **Add Reference** dialog box, click the **.NET** tab, select the **System.Data.Linq** assembly, and then click **OK**.  
  
     This assembly contains classes for using Language-Integrated Queries (LINQ). You will use LINQ to populate controls in the custom group with data from the Northwind database.  
  
3.  In **Solution Explorer**, click **CustomerRibbon.cs** or **CustomerRibbon.vb** to select it.  
  
4.  On the **View** menu, click **Code**.  
  
     The Ribbon code file opens in the Code Editor.  
  
5.  Add the following statements to the top of the Ribbon code file. These statements provide easy access to LINQ namespaces and to the namespace of the Outlook primary interop assembly (PIA).  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#1)]  
  
6.  Add the following code inside the CustomerRibbon class. This code declares the data table and table adapters that you will use to store information from the Customer, Orders, Order Details, and Product tables of the Northwind database.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#2)]  
  
7.  Add the following block of code to the `CustomerRibbon` class. This code adds three helper methods that create controls for the Ribbon at runtime.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#3)]  
  
8.  Replace the `CustomerRibbon_Load` event handler method with the following code. This code uses a LINQ query to perform the following tasks:  
  
    -   Populate the **Customers** combo box by using the ID and name of 20 customers in the Northwind database.  
  
    -   Calls the `PopulateSalesOrderInfo` helper method. This method updates the **ProductsPurchased** menu with sales order numbers that pertain to the currently selected customer.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#4)]  
  
9. Add the following code to the `CustomerRibbon` class. This code uses LINQ queries to perform the following tasks:  
  
    -   Adds a submenu to the **ProductsPurchased** menu for each sales order related to the selected customer.  
  
    -   Adds buttons to each submenu for the products related to the sales order.  
  
    -   Adds event handlers to each button.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#6)]  
  
10. In **Solution Explorer**, double-click the Ribbon code file.  
  
     The Ribbon Designer opens.  
  
11. In the Ribbon Designer, double-click the **Customers** combo box.  
  
     The Ribbon code file opens in the Code Editor, and the `ComboBox1_TextChanged` event handler appears.  
  
12. Replace the `ComboBox1_TextChanged` event handler with the following code. This code performs the following tasks:  
  
    -   Calls the `PopulateSalesOrderInfo` helper method. This method updates the **Products Purchased** menu with sales orders that relate to the selected customer.  
  
    -   Calls the `PopulateMailItem` helper method and passes in the current text, which is the selected customer name. This method populates the To, Subject, and Body fields of new mail messages.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#5)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#5)]  
  
13. Add the following Click event handler to the `CustomerRibbon` class. This code adds the name of selected products to the Body field of new mail messages.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#8)]  
  
14. Add the following code to the `CustomerRibbon` class. This code performs the following tasks:  
  
    -   Populates the To line of new mail messages by using the e-mail address of the currently selected customer.  
  
    -   Adds text to the Subject and Body fields of new mail messages.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/CSharp/Ribbon_Update_At_Runtime/CustomerRibbon.cs#7)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../vsto/codesnippet/VisualBasic/Ribbon_Update_At_Runtime/CustomerRibbon.vb#7)]  
  
## Testing the Controls in the Custom Group  
 When you open a new mail form in Outlook, a custom group named **Customer Purchases** appears on the **Messages** tab of the Ribbon.  
  
 To create a customer follow-up e-mail message, select a customer, and then select products purchased by the customer. The controls in the **Customer Purchases** group are updated at run time with data from the Northwind database.  
  
#### To test the controls in the custom group  
  
1.  Press F5 to run your project.  
  
     Outlook starts.  
  
2.  In Outlook, on the **File** menu, point to **New**, and then click **Mail Message**.  
  
     The following actions occur:  
  
    -   A new mail message Inspector window appears.  
  
    -   On the **Message** tab of the Ribbon, the **Customer Purchases** group appears before the **Clipboard** group.  
  
    -   The **Customers** combo box in the group is updated with the names of customers in the Northwind database.  
  
3.  On the **Message** tab of the Ribbon, in the **Customer Purchases** group, select a customer from the **Customers** combo box.  
  
     The following actions occur:  
  
    -   The **Products Purchased** menu is updated to show each sales order for the selected customer.  
  
    -   Each sales order submenu is updated to show the products purchased in that order.  
  
    -   The selected customer's e-mail address is added to the **To** line of the mail message, and the subject and body of the mail message are populated with text.  
  
4.  Click the **Products Purchases** menu, point to any sales order, and then click a product from the sales order.  
  
     The product name is added to the body of the mail message.  
  
## Next Steps  
 You can learn more about how to customize the Office UI from these topics:  
  
-   Add context-based UI to any document-level customization. For more information, see [Actions Pane Overview](../vsto/actions-pane-overview.md).  
  
-   Extend a standard or custom Microsoft Office Outlook form. For more information, see [Walkthrough: Designing an Outlook Form Region](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
-   Add a custom task pane to Outlook. For more information, see [Custom Task Panes](../vsto/custom-task-panes.md).  
  
## See Also  
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Ribbon Overview](../vsto/ribbon-overview.md)   
 [Language-Integrated Query (LINQ)](/dotnet/csharp/linq/index)   
 [How to: Get Started Customizing the Ribbon](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Ribbon Designer](../vsto/ribbon-designer.md)   
 [Walkthrough: Creating a Custom Tab by Using the Ribbon Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Ribbon Object Model Overview](../vsto/ribbon-object-model-overview.md)   
 [Customizing a Ribbon for Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [How to: Change the Position of a Tab on the Ribbon](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [How to: Customize a Built-in Tab](../vsto/how-to-customize-a-built-in-tab.md)   
 [How to: Add Controls to the Backstage View](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [How to: Export a Ribbon from the Ribbon Designer to Ribbon XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [How to: Show Add-in User Interface Errors](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  