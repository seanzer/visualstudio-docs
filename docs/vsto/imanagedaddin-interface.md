---
title: "IManagedAddin Interface | Microsoft Docs"
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
  - "IManagedAddin interface"
ms.assetid: 5350629c-6cf8-42dd-ae65-3f34322ee10f
caps.latest.revision: 11
author: "gewarren"
ms.author: "gewarren"
manager: "ghogen"
---
# IManagedAddin Interface
  Implement the IManagedAddin interface to create a component that loads managed VSTO Add-ins. This interface was added in the 2007 Microsoft Office system.  
  
## Syntax  
  
```  
[  
    object,  
    uuid(B9CEAB65-331C-4713-8410-DDDAF8EC191A),  
    pointer_default(unique),  
    oleautomation  
]  
interface IManagedAddin : IUnknown  
{  
    HRESULT Load(  
        [in] BSTR bstrManifestURL,   
        [in] IDispatch *pdispApplication);  
    HRESULT Unload();  
};  
```  
  
## Methods  
 The following table lists the methods that are defined by the IManagedAddin interface.  
  
|Name|Description|  
|----------|-----------------|  
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|Called when a Microsoft Office application loads a managed VSTO Add-in.|  
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Called just before a Microsoft Office application unloads a managed VSTO Add-in.|  
  
## Remarks  
 Microsoft Office applications, starting with the 2007 Microsoft Office system, use the IManagedAddin interface to help load Office VSTO Add-ins. You can implement the IManagedAddin interface to create your own VSTO Add-in loader and runtime for managed VSTO Add-ins, instead of using the VSTO Add-in loader (VSTOLoader.dll) and [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. For more information, see [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
## How Managed Add-ins Are Loaded  
 The following steps occur when an application starts:  
  
1.  The application discovers VSTO Add-ins by looking for entries under the following registry key:  
  
     HKEY_CURRENT_USER\Software\Microsoft\Office\\*\<application name>*\Addins\  
  
     Each entry under this registry key is a unique ID of the VSTO Add-in. Typically, this is the name of the VSTO Add-in assembly.  
  
2.  The application looks for a `Manifest` entry under the entry for each VSTO Add-in.  
  
     Managed VSTO Add-ins can store the full path of a manifest in the `Manifest` entry under HKEY_CURRENT_USER\Software\Microsoft\Office\\*\<application name>*\Addins\\*\<add-in ID>*. A manifest is a file (typically, an XML file) that provides information that is used to help load the VSTO Add-in.  
  
3.  If the application finds a `Manifest` entry, the application tries to load a managed VSTO Add-in loader component. The application does this by trying to create a COM object that implements the IManagedAddin interface.  
  
     The [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] includes an VSTO Add-in loader component (VSTOLoader.dll), or you can create your own by implementing the IManagedAddin interface.  
  
4.  The application calls the [IManagedAddin::Load](../vsto/imanagedaddin-load.md) method and passes in the value of the `Manifest` entry.  
  
5.  The [IManagedAddin::Load](../vsto/imanagedaddin-load.md) method performs tasks required to load the VSTO Add-in, such as configuring the application domain and security policy for the VSTO Add-in that is being loaded.  
  
 For more information about the registry keys that Microsoft Office applications use to discover and load managed VSTO Add-ins, see [Registry Entries for VSTO Add-ins](../vsto/registry-entries-for-vsto-add-ins.md).  
  
## Guidance for Implementing IManagedAddin  
 If you implement IManagedAddin, you must register the DLL that contains the implementation by using the following CLSID:  
  
 99D651D7-5F7C-470E-8A3B-774D5D9536AC  
  
 Microsoft Office applications use this CLSID to create the COM object that implements IManagedAddin.  
  
> [!CAUTION]  
>  This CLSID is also used by VSTOLoader.dll in the [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Therefore, if you use IManagedAddin to create your own VSTO Add-in loader and runtime component, you cannot deploy your component to computers that are running VSTO Add-ins that rely on the [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
## See Also  
 [Unmanaged API Reference &#40;Office Development in Visual Studio&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)  
  
  