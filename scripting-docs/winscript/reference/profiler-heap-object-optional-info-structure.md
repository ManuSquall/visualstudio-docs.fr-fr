---
title: "PROFILER_HEAP_OBJECT_OPTIONAL_INFO, structure | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 77e638bd-ae36-4292-a170-90a0c500e610
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# PROFILER_HEAP_OBJECT_OPTIONAL_INFO, structure
Représente les informations facultatives concernant les objets heap.  
  
## Syntaxe  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_OPTIONAL_INFO  
{  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE infoType;  
    [switch_type(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE), switch_is(infoType)] union  
    {  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_PROTOTYPE)] PROFILER_HEAP_OBJECT_ID prototype;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_FUNCTION_NAME)] LPCWSTR functionName;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_ATTRIBUTES_SIZE)] UINT elementAttributesSize;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_TEXT_CHILDREN_SIZE)] UINT elementTextChildrenSize;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_SCOPE_LIST)] PROFILER_HEAP_OBJECT_SCOPE_LIST* scopeList;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INTERNAL_PROPERTY)] PROFILER_HEAP_OBJECT_RELATIONSHIP* internalProperty;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_NAME_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* namePropertyList;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INDEX_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* indexPropertyList;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_RELATIONSHIPS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* relationshipList;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* eventList;  
    };  
} PROFILER_HEAP_OBJECT_OPTIONAL_INFO;  
  
```  
  
## Membres  
  
|Membre|Type|Description|  
|------------|----------|-----------------|  
|infoType|[PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_TYPE, énumération](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|Le type des informations facultatives.|  
|prototype|[PROFILER\_HEAP\_OBJECT\_ID, type](../../winscript/reference/profiler-heap-object-id-type.md)|L'ID de l'objet prototype de l'objet heap.|  
|functionName|LPCWSTR|La fonction de l'objet heap.|  
|elementAttributesSize|UINT|La taille des attributs de l'élément de l'objet heap.|  
|elementTextChildrenSize|UINT|La taille des enfants de texte de l'objet heap.|  
|scopeList|[PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST, structure](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|La liste de la portée de l'objet heap.|  
|internalProperty|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP, structure](../../winscript/reference/profiler-heap-object-relationship-structure.md)|La propriété interne de l'objet heap.|  
|namePropertyList|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST, structure](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|La liste des propriétés nom de l'objet heap.|  
|indexPropertyList|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST, structure](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|La liste des propriétés de l'index de l'objet heap.|  
|relationshipList|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST, structure](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Une liste des relations de l'objet heap.|  
|eventList|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST, structure](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Une liste des événements de l'objet heap.|