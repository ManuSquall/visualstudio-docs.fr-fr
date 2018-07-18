---
title: Profiler_heap_object_relationship_flags, énumération | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1a41b642-c9a9-4d83-b943-d59b232eebf6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab542225e0238dbd40f90d9de66d43d0791e05e0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734009"
---
# <a name="profilerheapobjectrelationshipflags-enumeration"></a>PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS, énumération
Indicateurs qui représentent des si un objet de tas pointé dans une relation d’objet est une méthode d’accesseur Get ou Set. Utilisé dans le [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) méthode lorsque la valeur PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS est spécifiée dans le `enumFlags` paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef [v1_enum] enum {    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR           = 0x00010000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR           = 0x00020000,} PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Valeur|Description|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE|0x00000000|Cet objet de segment de mémoire désigné dans une relation d’objet n’est pas identifié comme méthode d’une méthode getter ou setter.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR|0x00010000|L’objet de segment de mémoire désigné dans une relation d’objet est une méthode d’accesseur Get. Ces informations sont stockées dans les 2 octets (16 bits) haute de la [PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) champ.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR|0x00020000|L’objet de segment de mémoire désigné dans une relation d’objet est une méthode d’accesseur Set. Ces informations sont stockées dans les 2 octets (16 bits) haute de la `PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo` champ.|