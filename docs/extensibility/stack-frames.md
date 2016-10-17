---
title: "Stack Frames"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: na
ms.topic: "article"
helpviewer_keywords: 
  - "stack frames, debugging"
  - "debugging [Debugging SDK], stack frames"
  - "stack frames"
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
translation.priority.mt: 
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
# Stack Frames
In terms of the debugger architecture, a **stack frame**:  
  
-   Is an abstraction of a stack that provides the execution context of a thread. A thread always executes within a function. A stack frame holds the local variables of the function, and the arguments to it. In order to debug with Visual Studio, the language or environment being debugged must support stack frames.  
  
-   Can both identify and describe itself, and can return the associated thread. A stack frame can also return the code context that represents the current instruction pointer, as well as the associated documentation and expression evaluation contexts.  
  
-   Has properties that describe the name, type, and value of local variables and arguments, and which appear in various IDE debug windows.  
  
-   Is represented by an [IDebugStackFrame2](../extensibility/idebugstackframe2.md) interface, typically created by a debug engine (DE) or virtual machine as a consequence of executing a thread.  
  
## See Also  
 [Debugger Contexts](../extensibility/debugger-contexts.md)   
 [Debugger Concepts](../extensibility/debugger-concepts.md)   
 [Debug Engine](../extensibility/debug-engine.md)   
 [IDebugStackFrame2](../extensibility/idebugstackframe2.md)