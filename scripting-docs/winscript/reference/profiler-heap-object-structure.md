---
title: "PROFILER_HEAP_OBJECT, structure | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 9f35362c-6856-4cfb-b990-031a156a58eb
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_HEAP_OBJECT, structure
Représente les objets heap rassemblés par [IActiveScriptProfilerControl3::EnumHeap, méthode](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## Syntaxe  
  
```  
typedef struct _PROFILER_HEAP_OBJECT  
{  
    UINT size;  
    union {  
        PROFILER_HEAP_OBJECT_ID objectId;  
        PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;  
    };  
    PROFILER_HEAP_OBJECT_NAME_ID typeNameId;  
    USHORT flags;   
    USHORT optionalInfoCount;  
} PROFILER_HEAP_OBJECT;  
```  
  
## Membres  
  
|Membre|Type|Description|  
|------------|----------|-----------------|  
|objectId|[PROFILER\_HEAP\_OBJECT\_ID, type](../../winscript/reference/profiler-heap-object-id-type.md)|L'ID de l'objet heap.|  
|externalObjectAddress|[PROFILER\_EXTERNAL\_OBJECT\_ADDRESS, type](../../winscript/reference/profiler-external-object-address-type.md)|L'adresse de l'objet externe d'un objet, tel que l'objet C\/C\+\+ \+\+\-allocated, qui est en dehors de le tas JavaScript.|  
|typeNameId|[PROFILER\_HEAP\_OBJECT\_NAME\_ID, type](../../winscript/reference/profiler-heap-object-name-id-type.md)|L'ID du type d'objet heap nom, extrait d' [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md).  Un seul d' `externalObjectAddress` ou d' `typeName` est présent selon la valeur d' `flags` .|  
|balises|[PROFILER\_HEAP\_OBJECT\_FLAGS, énumération](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Les balises qui contiennent des informations de base sur l'objet heap.|  
|optionalInfoCount|USHORT|Le nombre d'enregistrements de [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO, structure](../../winscript/reference/profiler-heap-object-optional-info-structure.md) qui sont disponibles pour l'objet heap.|