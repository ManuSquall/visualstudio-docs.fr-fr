---
title: "PROFILER_RELATIONSHIP_INFO, &#233;num&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: fae69317-6224-4a6a-8e9e-ccaa6a330818
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# PROFILER_RELATIONSHIP_INFO, &#233;num&#233;ration
Représente les informations sur l'objet dans la relation.  Utilisé dans [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP, structure](../../winscript/reference/profiler-heap-object-relationship-structure.md).  
  
## Syntaxe  
  
```  
typedef [v1_enum] enum {  
    PROFILER_PROPERTY_TYPE_NUMBER = 0x01,  
    PROFILER_PROPERTY_TYPE_STRING = 0x02,  
    PROFILER_PROPERTY_TYPE_HEAP_OBJECT = 0x03,  
    PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT = 0x04,  
    PROFILER_PROPERTY_TYPE_BSTR = 0x05,  
} PROFILER_RELATIONSHIP_INFO;  
  
```  
  
## Membres  
  
|Membre|Valeur|Description|  
|------------|------------|-----------------|  
|PROFILER\_PROPERTY\_TYPE\_NUMBER|0x01|L'objet est un nombre.|  
|PROFILER\_PROPERTY\_TYPE\_STRING|0x02|l'objet est une chaîne.|  
|PROFILER\_PROPERTY\_TYPE\_HEAP\_OBJECT|0x03|l'objet est un objet heap.|  
|PROFILER\_PROPERTY\_TYPE\_EXTERNAL\_OBJECT|0x04|L'objet est externe, c. autrement dit., pas sur le tas de garbage collection.|  
|PROFILER\_PROPERTY\_TYPE\_BSTR|0x05|L'objet est un BSTR.|