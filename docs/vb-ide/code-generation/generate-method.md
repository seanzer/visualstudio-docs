---
title: "Generate a method - Code Generation (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 683790b4-b68b-42d7-8dc4-a68eca05aa01
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
translation.priority.ht: 
  - "cs-cz"
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pl-pl"
  - "pt-br"
  - "ru-ru"
  - "tr-tr"
  - "zh-cn"
  - "zh-tw"
---

# Generate a method in Visual Basic
**What:** Lets you immediately add a method to a class. 

**When:** You introduce a new method and want to properly declare it, automatically.  

**Why:** You could declare the method and parameters before using it, however this feature will generate the declaration automatically. 

**How:**

1. Place your cursor on the line where there is a red squiggle indicating you've used a method that doesn't yet exist.

   ![Highlighted code](media/method_highlight.png)

1. Next, do one of the following:
   * **Keyboard**
     * Press **Ctrl+.** to trigger the **Quick Actions and Refactorings** menu and select **Generate method** from the Preview window popup.
   * **Mouse**
     * Right-click and select the **Quick Actions and Refactorings** menu and select **Generate method** from the Preview window popup.
     * Hover over the red squiggle and click the ![Lightbulb](media/bulb.png) icon which appears.
     * Click the ![Lightbulb](media/bulb.png) icon which appears in the left margin if the text cursor is already on the line with the red squiggle.

   ![Generate method preview](media/method_preview.png)

   >[!TIP]
   >Use the [**Preview changes**](../../ide/preview-changes.md) link at the bottom of the preview window to see all of the changes that will be made before making your selection.

1. The method will be created automatically with any parameters inferred from its usage.

   ![Generate method result](media/method_result.png)
  
## See Also  
[Code Generation (Visual Basic)](../code-generation-vb.md)  
[Preview Changes](../../ide/preview-changes.md)