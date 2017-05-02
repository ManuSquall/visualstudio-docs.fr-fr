---
title: "PROFILER_HEAP_OBJECT_RELATIONSHIP, structure | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 3ab3d986-3314-4c7b-a1c8-18ed691a8b9c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_HEAP_OBJECT_RELATIONSHIP, structure
Représente une relation d'un objet heap.  
  
## Syntaxe  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_RELATIONSHIP  
{  
    PROFILER_HEAP_OBJECT_NAME_ID relationshipId;  
    PROFILER_RELATIONSHIP_INFO relationshipInfo;  
    [switch_type(PROFILER_RELATIONSHIP_INFO), switch_is(relationshipInfo)] union  
    {  
        [case(PROFILER_PROPERTY_TYPE_NUMBER)] double numberValue;  
        [case(PROFILER_PROPERTY_TYPE_STRING)] LPCWSTR stringValue;  
        [case(PROFILER_PROPERTY_TYPE_HEAP_OBJECT)] PROFILER_HEAP_OBJECT_ID objectId;  
        [case(PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT)] PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;  
    };  
} PROFILER_HEAP_OBJECT_RELATIONSHIP;  
  
```  
  
## Membres  
  
|Membre|Valeur|Description|  
|------------|------------|-----------------|  
|relationshipId|[PROFILER\_HEAP\_OBJECT\_NAME\_ID, type](../../winscript/reference/profiler-heap-object-name-id-type.md)|L'ID du nom de la relation, d' [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md).|  
|relationshipInfo|[PROFILER\_RELATIONSHIP\_INFO, énumération](../../winscript/reference/profiler-relationship-info-enumeration.md)|Informations sur la relation.|  
|numberValue|double|La valeur du nombre.  Un seul d' `numberValue`\/`stringValue`\/`objectId`\/`externalObjectAddress` est défini, selon la valeur d' `relationshipInfo` .|  
|stringValue|LPCWSTR|Valeur de chaîne.|  
|objectId|[PROFILER\_HEAP\_OBJECT\_ID, type](../../winscript/reference/profiler-heap-object-id-type.md)|L'ID de l'objet heap.|  
|externalObjectAddress|[PROFILER\_EXTERNAL\_OBJECT\_ADDRESS, type](../../winscript/reference/profiler-external-object-address-type.md)|l'adresse externe d'objet.|