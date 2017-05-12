---
title: "PROFILER_HEAP_OBJECT_FLAGS, &#233;num&#233;ration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 0f517743-cc4a-4911-add3-a43680071a1f
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# PROFILER_HEAP_OBJECT_FLAGS, &#233;num&#233;ration
Balises qui représentent des informations de base sur l'objet heap.  Utilisé dans [PROFILER\_HEAP\_OBJECT, structure](../../winscript/reference/profiler-heap-object-structure.md).  
  
## Syntaxe  
  
```  
typedef [v1_enum] enum {  
    PROFILER_HEAP_OBJECT_FLAGS_NEW_OBJECT            = 0x00000001,  
    PROFILER_HEAP_OBJECT_FLAGS_IS_ROOT               = 0x00000002,  
    PROFILER_HEAP_OBJECT_FLAGS_SITE_CLOSED           = 0x00000004,  
    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL              = 0x00000008,  
    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_UNKNOWN      = 0x00000010,  
    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_DISPATCH     = 0x00000020,  
    PROFILER_HEAP_OBJECT_FLAGS_SIZE_APPROXIMATE      = 0x00000040,  
    PROFILER_HEAP_OBJECT_FLAGS_SIZE_UNAVAILABLE      = 0x00000080,  
    PROFILER_HEAP_OBJECT_FLAGS_NEW_STATE_UNAVAILABLE = 0x00000100,  
    PROFILER_HEAP_OBJECT_FLAGS_WINRT_INSTANCE        = 0x00000200,  
    PROFILER_HEAP_OBJECT_FLAGS_WINRT_RUNTIMECLASS    = 0x00000400,  
    PROFILER_HEAP_OBJECT_FLAGS_WINRT_DELEGATE        = 0x00000800,  
    PROFILER_HEAP_OBJECT_FLAGS_WINRT_NAMESPACE       = 0x00001000,  
} PROFILER_HEAP_OBJECT_FLAGS;  
  
```  
  
## Membres  
  
|Membre|Valeur|Description|  
|------------|------------|-----------------|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_NEW\_OBJECT|0x00000001|Cet objet heap a été alloué après que la requête précédente d'énumération du tas.  Les valeurs de[PROFILER\_HEAP\_OBJECT\_ID, type](../../winscript/reference/profiler-heap-object-id-type.md) peuvent être réutilisées si l'objet est collecté.|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_IS\_ROOT|0x00000002|Cet objet heap est un objet racine du graphique d'objet.|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_SITE\_CLOSED|0x00000004|Cet objet est heap d'un site de script qui a été fermé.|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_EXTERNAL|0x00000008|Cet objet heap a été alloué à l'extérieur de le tas de garbage collection JavaScript.|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_EXTERNAL\_UNKNOWN|0x00000010|Cet objet heap a été alloué à l'extérieur de le tas de garbage collection et implémente IUnknown.|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_EXTERNAL\_DISPATCH|0x00000020|Cet objet heap a été alloué à l'extérieur de le tas de garbage collection et implémente l'interface d'IDISPATCH.|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_SIZE\_APPROXIMATE|0x00000040|La taille de cet objet est heap approximative.|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_SIZE\_UNAVAILABLE|x00000080|La taille de cet objet heap est pas disponible.|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_WINRT\_INSTANCE|0x00000200|L'objet heap est une instance d'exécution windows.|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_WINRT\_RUNTIMECLASS|0x00000400|L'objet heap est une classe d'exécution du windows.|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_WINRT\_DELEGATE|0x00000800|L'objet heap est un délégué d'exécution windows.|  
|PROFILER\_HEAP\_OBJECT\_FLAGS\_WINRT\_NAMESPACE|0x00001000|L'objet heap est dans l'espace de noms du windows.|