---
title: "IDebugApplicationThread110::IsThreadCallable | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread110::IsThreadCallable"
ms.assetid: 2a75a366-801d-47e0-bba3-51aa669e03a7
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplicationThread110::IsThreadCallable
Détermine si ce thread est dans un état qui gérera les appels effectués à l'aide de mécanismes de basculement du thread du PDM, tels que SynchronousCallInThread.  
  
> [!IMPORTANT]
>  [IDebugApplicationThread110 \(interface\)](../../winscript/reference/idebugapplicationthread110-interface.md) est implémenté par PDM v11.0 et supérieur.  Trouvé dans activdbg100.h.  
  
## Syntaxe  
  
```cpp  
HRESULT IsThreadCallable([out, annotation("_Out_")] BOOL * pfIsCallable);  
```  
  
#### Paramètres  
 `pfIsCallable`  
 \[out\]  `true` si le thread est appelé, sinon `false`.  
  
## Voir aussi  
 [IDebugApplicationThread110 \(interface\)](../../winscript/reference/idebugapplicationthread110-interface.md)