---
title: "PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE, &#233;num&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: fcb55f5f-ce75-4d05-9ce9-ba28c622f97d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE, &#233;num&#233;ration
Représente les différents types d'informations facultatives.  Utilisé dans [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO, structure](../../winscript/reference/profiler-heap-object-optional-info-structure.md).  
  
## Syntaxe  
  
```  
typedef [v1_enum] enum {  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_PROTOTYPE                    = 0x00000001,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_FUNCTION_NAME                = 0x00000002,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_SCOPE_LIST                   = 0x00000003,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INTERNAL_PROPERTY            = 0x00000004,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_NAME_PROPERTIES              = 0x00000005,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INDEX_PROPERTIES             = 0x00000006,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_ATTRIBUTES_SIZE      = 0x00000007,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_TEXT_CHILDREN_SIZE   = 0x00000008,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_RELATIONSHIPS                = 0x00000009,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS                  = 0x0000000A,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_MAX_VALUE                    = PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS  
} PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE;  
  
```  
  
## Membres  
  
|Membre|Valeur|Description|  
|------------|------------|-----------------|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_PROTOTYPE|0x00000001|Informations sur le prototype de l'objet heap.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_FUNCTION\_NAME|0x00000002|Informations sur la fonction de l'objet heap.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_SCOPE\_LIST|0x00000003|Informations sur [PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST, structure](../../winscript/reference/profiler-heap-object-scope-list-structure.md)de l'objet heap.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_INTERNAL\_PROPERTY|0x00000004|Informations sur la propriété interne de l'objet heap.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_NAME\_PROPERTIES|0x00000005|Informations sur les propriétés nom de l'objet heap.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_INDEX\_PROPERTIES|0x00000006|Informations sur les propriétés de l'index de l'objet heap.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_ELEMENT\_ATTRIBUTES\_SIZE|0x00000007|La taille des attributs associés à un élément DOM.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_ELEMENT\_TEXT\_CHILDREN\_SIZE|0x00000008|La taille de tout texte associé à un élément DOM.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_RELATIONSHIPS|0x00000009|Informations sur les relations de l'objet heap.|  
|ROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_WINRTEVENTS|0x0000000A|Informations sur les événements de runtime windows de l'objet heap.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_MAX\_VALUE|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_WINRTEVENTS|La valeur maximale de cette énumération.|