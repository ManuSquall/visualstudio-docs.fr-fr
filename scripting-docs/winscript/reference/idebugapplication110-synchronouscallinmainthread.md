---
title: "IDebugApplication110::SynchronousCallInMainThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplication110::SynchronousCallInMainThread"
ms.assetid: 57475ae5-1520-45ef-800d-ccfc6235a5d1
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplication110::SynchronousCallInMainThread
Effectue un appel synchrone sur le thread principal.  
  
> [!IMPORTANT]
>  [IDebugApplication110 \(interface\)](../../winscript/reference/idebugapplication110-interface.md) est implémenté par PDM v11.0 et supérieur.  Trouvé dans activdbg100.h.  
  
## Syntaxe  
  
```cpp  
HRESULT SynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
  
```  
  
#### Paramètres  
 `pptc`  
 l'objet d' [IDebugThreadCall, interface](../../winscript/reference/idebugthreadcall-interface.md) à l'appel.  
  
 `dwParam1`  
 Le premier paramètre de l'appel.  
  
 `dwParam1`  
 Le premier paramètre de l'appel.  
  
 `dwParam2`  
 Le second paramètre de l'appel.  
  
 `dwParam3`  
 Le troisième paramètre de l'appel.  
  
## Voir aussi  
 [IDebugApplication110 \(interface\)](../../winscript/reference/idebugapplication110-interface.md)