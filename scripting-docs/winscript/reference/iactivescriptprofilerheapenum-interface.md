---
title: "IActiveScriptProfilerHeapEnum, interface | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 16756d0e-547a-4825-8b7b-a7e0e4708a04
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptProfilerHeapEnum, interface
Un itérateur sur les objets heap associés à un moteur de script, rassemblé par [IActiveScriptProfilerControl3::EnumHeap, méthode](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## Syntaxe  
  
```vb  
interface IActiveScriptProfilerHeapEnum : IUnknown  
```  
  
## Méthodes  
 [IActiveScriptProfilerHeapEnum::Next, méthode](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)  
 Obtient le suivants objet ou objets dans l'ensemble d'objets heap rassemblés par [IActiveScriptProfilerControl3::EnumHeap, méthode](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
 [IActiveScriptProfilerHeapEnum::GetOptionalInfo, méthode](../../winscript/reference/iactivescriptprofilerheapenum-getoptionalinfo-method.md)  
 Obtient les informations facultatives sur l'objet spécifié dans l'ensemble d'objets heap rassemblés par [IActiveScriptProfilerControl3::EnumHeap, méthode](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
 [IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo, méthode](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md)  
 Libère les structures spécifiées de [PROFILER\_HEAP\_OBJECT, structure](../../winscript/reference/profiler-heap-object-structure.md) et leurs éléments associés de [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO, structure](../../winscript/reference/profiler-heap-object-optional-info-structure.md) .  
  
 [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md)  
 Retourne les noms de chaîne correspondant aux valeurs de [PROFILER\_HEAP\_OBJECT\_NAME\_ID, type](../../winscript/reference/profiler-heap-object-name-id-type.md) .