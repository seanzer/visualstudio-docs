---
title: "&lt;update&gt; Element (Office Development in Visual Studio) | Microsoft Docs"
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
  - "update element"
  - "<update> element"
  - "application manifests [Office development in Visual Studio], <update> element"
ms.assetid: bdd5dbf7-ddda-4ef6-9db5-1fb4405261a0
caps.latest.revision: 24
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# &lt;update&gt; Element (Office Development in Visual Studio)
  The `update` element specifies the interval at which the solution will check for updates.  
  
## Syntax  
  
```  
<update  
  enabled>  
  <expiration  
    maximumAge  
    unit  
  />  
</update>  
```  
  
## Elements and Attributes  
 The `update` element is required and is in the `vstav3` namespace.  
  
 The `update` element has the following attributes.  
  
|Attribute|Description|  
|---------------|-----------------|  
|`enabled`|Required. Set enabled to one of the following values:<br /><br /> -   **true** to check for updates.<br />-   **false** to prevent checking for updates.|  
  
 The `update` element has the following child elements.  
  
### expiration  
 The `expiration` element is required and is in the `vstav3` namespace. This element specifies the interval at which the solution checks for updates.  
  
 The `expiration` element has the following attributes.  
  
|Attribute|Description|  
|---------------|-----------------|  
|`maximumAge`|-   Required. Set this equal to an integer.|  
|`unit`|Required. Set `unit` to one of the following values:<br /><br /> -   **hours**<br />-   **days**<br />-   **weeks**|  
  
## Example of Always Checking for Updates  
  
### Description  
 The following code example illustrates an `update` element that is set to always check for updates in Office solutions.  
  
### Code  
  
```  
<vstav3:update enabled="true" />  
```  
  
## Example of Setting a Default Update Interval  
  
### Description  
 The following code example illustrates an `update` element in an application manifest for Office solutions. This code example is part of a larger example provided in [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:update enabled="true">  
    <vstav3:expiration maximumAge="7" unit="days" />  
</vstav3:update>  
```  
  
## See Also  
 [Deploying an Office Solution by Using ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Deployment Manifests for Office Solutions](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  