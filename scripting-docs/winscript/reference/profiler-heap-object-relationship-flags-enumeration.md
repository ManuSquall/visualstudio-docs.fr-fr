---
title: Énumération PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1a41b642-c9a9-4d83-b943-d59b232eebf6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 322f6f3352c1b0dfad4572d55e1ebe2388c8cc4a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823632"
---
# <a name="profilerheapobjectrelationshipflags-enumeration"></a>PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS, énumération
Indicateurs qui représentent si un objet de segment de mémoire désigné dans une relation entre objets sont une méthode getter ou setter. Utilisé dans le [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) méthode lorsque la valeur PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS est spécifiée dans le `enumFlags` paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef [v1_enum] enum {    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR           = 0x00010000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR           = 0x00020000,} PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Value|Description|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE|0x00000000|Cet objet segment de mémoire désigné dans une relation d’objet n’est pas identifié comme méthode d’une méthode getter ou setter.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR|0x00010000|L’objet de tas ciblé dans une relation entre objets est une méthode d’accesseur Get. Ces informations seront stockées dans les 2 octets (16 bits) de la [PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) champ.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR|0x00020000|L’objet de tas ciblé dans une relation entre objets est une méthode d’accesseur Set. Ces informations seront stockées dans les 2 octets (16 bits) de la `PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo` champ.|