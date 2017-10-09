---
title: "&lt;formRegion&gt; Element (Office Development in Visual Studio) | Microsoft Docs"
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
  - "application manifests [Office development in Visual Studio], <formRegion> element"
ms.assetid: d397cf31-c0ef-47f0-860a-cd816e4bf6eb
caps.latest.revision: 23
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# &lt;formRegion&gt; Element (Office Development in Visual Studio)
  The `formRegion` element of the `vstov4` namespace identifies a Microsoft Office Outlook form region that is associated with an VSTO Add-in.  
  
## Syntax  
  
```  
<formRegion  
  name>  
  <messageClass  
    name/>  
</formRegion>  
```  
  
## Elements and Attributes  
 The `formRegion` element of the `vstov4` namespace identifies a form region that is associated with an Outlook VSTO Add-in. It is required only for Outlook VSTO Add-ins that include form regions.  
  
 There can be multiple `formRegion` elements defined inside a `formRegions` element for a single VSTO Add-in.  
  
 The `formRegion` element has the following attribute.  
  
|Attribute|Description|  
|---------------|-----------------|  
|`name`|Required. Identifies the form region name.|  
  
 The `formRegion` element has the following child elements.  
  
### messageClass  
 The `messageClass` element identifies the Outlook form that is associated with the form region.  
  
 The `messageClass` element has the following attribute.  
  
|Attribute|Description|  
|---------------|-----------------|  
|`name`|Required. Identifies the form that is associated with the form region.|  
  
## Example  
 The following code example illustrates a `formRegion` element in an application manifest for an Outlook VSTO Add-in deployed using [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. There are three message classes associated with this one form region. This code example is part of a larger example provided in [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<vstov4:formRegion  
    name="OutlookAddIn1.FormRegion1">  
  <vstov4:messageClass name="IPM.Note" />  
  <vstov4:messageClass name="IPM.Contact" />  
  <vstov4:messageClass name="IPM.Appointment" />  
</vstov4:formRegion>  
```  
  
## See Also  
 [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md)   
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Deployment Manifests for Office Solutions](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  