---
title: "PROFILER_HEAP_OBJECT_SCOPE_LIST, structure | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 33ebaa31-0a35-47d5-a4e3-afd83e16f53e
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# PROFILER_HEAP_OBJECT_SCOPE_LIST, structure
Cette structure est associée aux objets de fonction uniquement.  La liste de portée représente la fermeture de la fonction comme une liste de portées où chaque portée est un objet heap avec une liste de propriétés associée qui représente des variables dans chaque portée donnée.  Dans certains cas, les noms des objets dans cette portée peuvent ne pas être disponibles, ainsi que leur index dans la liste de propriétés est disponible.  
  
## Syntaxe  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_SCOPE_LIST  
{  
    UINT count;  
    [size_is(count)] PROFILER_HEAP_OBJECT_ID scopes[];  
} PROFILER_HEAP_OBJECT_SCOPE_LIST;  
  
```  
  
## Membres  
  
|Membre|Type|Description|  
|------------|----------|-----------------|  
|count|UINT|Le nombre de portées|  
|scopes|[PROFILER\_HEAP\_OBJECT\_ID, type](../../winscript/reference/profiler-heap-object-id-type.md)|Un tableau de portées.|