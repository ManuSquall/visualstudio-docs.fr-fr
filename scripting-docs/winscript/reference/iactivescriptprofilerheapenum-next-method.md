---
title: "IActiveScriptProfilerHeapEnum::Next, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 0336286f-1dcd-4df9-adf5-76b59b4e74bb
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IActiveScriptProfilerHeapEnum::Next, m&#233;thode
Obtient le suivants objet ou objets dans l'ensemble d'objets heap d' [IActiveScriptProfilerControl3::EnumHeap, méthode](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## Syntaxe  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] PROFILER_HEAP_OBJECT** heapObjects,   
    [out] ULONG *pceltFetched);  
  
```  
  
#### Paramètres  
 `celt`  
 Nombre d'objets à retourner.  
  
 `heapObjects`  
 \[out\]  Les structures suivantes de [PROFILER\_HEAP\_OBJECT, structure](../../winscript/reference/profiler-heap-object-structure.md) .  
  
 `pceltFetched`  
 \[out\]  le nombre d'objets retournés,  
  
## Valeur de retour  
 HRESULT.