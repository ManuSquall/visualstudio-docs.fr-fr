---
title: "IActiveScriptProfilerHeapEnum::GetOptionalInfo, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 99ed9df5-71cf-4c25-b189-af9accc466ee
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptProfilerHeapEnum::GetOptionalInfo, m&#233;thode
Obtient les informations facultatives sur l'objet spécifié \(de l'ensemble d'objets soucier retournés d'[IActiveScriptProfilerControl3::EnumHeap, méthode](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)\).  
  
 Vous ne devez pas libérer la mémoire retournée assignée aux objets retournés.  À la place, vous devez appeler [IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo, méthode](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md).  
  
## Syntaxe  
  
```  
HRESULT GetOptionalInfo (  
    [in] PROFILER_HEAP_OBJECT* heapObject,  
    [in] ULONG celt,  
    [out, size_is(celt)] PROFILER_HEAP_OBJECT_OPTIONAL_INFO* optionalInfo);  
  
```  
  
#### Paramètres  
 `heapObject`  
 [PROFILER\_HEAP\_OBJECT, structure](../../winscript/reference/profiler-heap-object-structure.md) pour lequel retourner les informations.  
  
 `celt`  
 Nombre de structures [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO, structure](../../winscript/reference/profiler-heap-object-optional-info-structure.md) à retourner.  
  
 `optionalInfo`  
 \[out\] un tableau de structures [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO, structure](../../winscript/reference/profiler-heap-object-optional-info-structure.md) pour l'objet spécifié.  
  
## Valeur de retour  
 HRESULT.