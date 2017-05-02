---
title: "IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: fdd5f7cc-be4e-4c13-a181-6320d26b44eb
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo, m&#233;thode
Libère les structures spécifiées de [PROFILER\_HEAP\_OBJECT, structure](../../winscript/reference/profiler-heap-object-structure.md) et leurs éléments associés de [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO, structure](../../winscript/reference/profiler-heap-object-optional-info-structure.md) .  
  
## Syntaxe  
  
```  
HRESULT FreeObjectAndOptionalInfo (  
    [in] ULONG celt,  
    [in, size_is(celt)] PROFILER_HEAP_OBJECT** heapObjects);  
  
```  
  
#### Paramètres  
 `celt`  
 Le nombre d'objets à libérer.  
  
 `heapObjects`  
 Tableau de structures [PROFILER\_HEAP\_OBJECT, structure](../../winscript/reference/profiler-heap-object-structure.md).  
  
## Valeur de retour  
 HRESULT.