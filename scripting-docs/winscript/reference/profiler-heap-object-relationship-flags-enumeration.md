---
title: "PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS, &#233;num&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 1a41b642-c9a9-4d83-b943-d59b232eebf6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS, &#233;num&#233;ration
Indicateurs qui représentent si un objet segment de mémoire désigné dans une relation d'objet est une méthode getter ou setter.  Utilisé dans la méthode [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) lorsque la valeur de PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS est spécifiée dans le paramètre `enumFlags`.  
  
## Syntaxe  
  
```  
typedef [v1_enum] enum {  
    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE                      = 0x00000000,  
    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR           = 0x00010000,  
    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR           = 0x00020000,  
} PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS;  
  
```  
  
## Membres  
  
|Membre|Valeur|Description|  
|------------|------------|-----------------|  
|PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS\_NONE|0x00000000|Cet objet segment de mémoire désigné dans une relation entre objets n'est pas reconnu comme méthode d'accesseur Get ou d'accesseur Set.|  
|PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS\_IS\_GET\_ACCESSOR|0x00010000|L'objet de tas ciblé dans une relation entre objets est une méthode d'accesseur Get.  Ces informations sont stockées dans la réalisation de 2 octets \(16 bits\) du champ d'[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS\_IS\_SET\_ACCESSOR|0x00020000|L'objet de tas ciblé dans une relation entre objets est une méthode setter.  Ces informations sont stockées dans la réalisation de 2 octets \(16 bits\) du champ `PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo`.|