---
title: "PROFILER_HEAP_OBJECT_FLAGS, &#233;num&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 17936b7a-40d5-4774-b92b-b24ee391591e
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_HEAP_OBJECT_FLAGS, &#233;num&#233;ration
Indicateurs qui représentent si des informations supplémentaires relatives à un objet segment de mémoire désigné dans une relation d'objet est exposée.  Utilisé dans la méthode [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md).  
  
## Syntaxe  
  
```  
typedef [v1_enum] enum {  
    PROFILER_HEAP_ENUM_FLAGS_NONE                      = 0x00000000,  
    PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS  = 0x00000001,  
} PROFILER_HEAP_ENUM_FLAGS;  
  
```  
  
## Membres  
  
|Membre|Valeur|Description|  
|------------|------------|-----------------|  
|PROFILER\_HEAP\_ENUM\_FLAGS\_NONE|0x00000000|Cet objet segment de mémoire n'expose pas d'informations supplémentaires à propos d'une relation entre objets.  Cet objet soucier se comporte de la même façon qu' [IActiveScriptProfilerControl3::HeapEnum](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|PROFILER\_HEAP\_ENUM\_ENUM\_ STORE\_RELATIONSHIP\_FLAGS|0x00000001|Cet objet segment de mémoire expose des informations sur le fait qu'un objet désigné dans une relation entre objets est une méthode d'accesseur Get ou d'accesseur Set.  Ces informations sont stockées dans la réalisation de 2 octets \(16 bits\) du champ d'[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) comme une des valeurs d'énumération [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS](../../winscript/reference/profiler-heap-object-relationship-flags-enumeration.md).|