---
title: "Profiler_heap_object_flags, énumération | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 0f517743-cc4a-4911-add3-a43680071a1f
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 96e05d67bedcf03c97edc1015c80b212b6021562
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="profilerheapobjectflags-enumeration"></a>PROFILER_HEAP_OBJECT_FLAGS, énumération
Indicateurs qui représentent des informations de base sur l’objet de tas. Utilisé dans le [profiler_heap_object, Structure](../../winscript/reference/profiler-heap-object-structure.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef [v1_enum] enum {    PROFILER_HEAP_OBJECT_FLAGS_NEW_OBJECT            = 0x00000001,    PROFILER_HEAP_OBJECT_FLAGS_IS_ROOT               = 0x00000002,    PROFILER_HEAP_OBJECT_FLAGS_SITE_CLOSED           = 0x00000004,    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL              = 0x00000008,    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_UNKNOWN      = 0x00000010,    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_DISPATCH     = 0x00000020,    PROFILER_HEAP_OBJECT_FLAGS_SIZE_APPROXIMATE      = 0x00000040,    PROFILER_HEAP_OBJECT_FLAGS_SIZE_UNAVAILABLE      = 0x00000080,    PROFILER_HEAP_OBJECT_FLAGS_NEW_STATE_UNAVAILABLE = 0x00000100,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_INSTANCE        = 0x00000200,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_RUNTIMECLASS    = 0x00000400,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_DELEGATE        = 0x00000800,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_NAMESPACE       = 0x00001000,} PROFILER_HEAP_OBJECT_FLAGS;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Valeur|Description|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_OBJECT_FLAGS_NEW_OBJECT|0x00000001|Cet objet de segment de mémoire a été alloué après la précédente demande d’énumération du tas. [Profiler_heap_object_id, Type](../../winscript/reference/profiler-heap-object-id-type.md) valeurs peuvent être réutilisées si l’objet est collecté.|  
|PROFILER_HEAP_OBJECT_FLAGS_IS_ROOT|0x00000002|Cet objet de segment de mémoire est un objet racine du graphique d’objets.|  
|PROFILER_HEAP_OBJECT_FLAGS_SITE_CLOSED|0x00000004|Cet objet de segment de mémoire est d’un site de script qui a été fermé.|  
|PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL|0x00000008|Cet objet de segment de mémoire a été alloué à l’extérieur de tas de garbage collection JavaScript.|  
|PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_UNKNOWN|0x00000010|Cet objet de segment de mémoire a été alloué à l’extérieur du tas de garbage collection et la met en œuvre IUnknown.|  
|PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_DISPATCH|0x00000020|Cet objet de segment de mémoire a été alloué à l’extérieur de tas de garbage collection et implémente l’interface IDISPATCH.|  
|PROFILER_HEAP_OBJECT_FLAGS_SIZE_APPROXIMATE|0x00000040|La taille de cet objet de segment de mémoire est approximative.|  
|PROFILER_HEAP_OBJECT_FLAGS_SIZE_UNAVAILABLE|x00000080|La taille de cet objet de segment de mémoire n’est pas disponible.|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_INSTANCE|0x00000200|L’objet de segment de mémoire est une instance d’exécution de Windows.|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_RUNTIMECLASS|0x00000400|L’objet de segment de mémoire est une classe d’exécution Windows Runtime.|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_DELEGATE|0x00000800|L’objet de segment de mémoire est un délégué Windows Runtime.|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_NAMESPACE|0x00001000|L’objet de tas est dans l’espace de noms Windows Runtime.|