---
title: Profiler_heap_object_flags, énumération | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 17936b7a-40d5-4774-b92b-b24ee391591e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d613ed3bcb4699f20d521f08b6c34d55d8363ba4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830355"
---
# <a name="profilerheapenumflags-enumeration"></a>PROFILER_HEAP_OBJECT_FLAGS, énumération
Indicateurs qui représentent si des informations supplémentaires sur un objet de tas ciblé dans une relation entre objets sont exposées. Utilisé dans le [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef [v1_enum] enum {    PROFILER_HEAP_ENUM_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS  = 0x00000001,} PROFILER_HEAP_ENUM_FLAGS;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Value|Description|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_ENUM_FLAGS_NONE|0x00000000|Cet objet segment de mémoire n’expose pas d’informations supplémentaires sur une relation entre objets. Cet objet segment de mémoire se comporte de la même façon que [IActiveScriptProfilerControl3::HeapEnum](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|PROFILER_HEAP_ENUM_ENUM_ STORE_RELATIONSHIP_FLAGS|0x00000001|Cet objet segment de mémoire expose des informations sur ou non un objet désigné dans une relation entre objets est une méthode getter ou setter. Ces informations seront stockées dans les 2 octets (16 bits) de la [PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) champ comme l’un de le [PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS](../../winscript/reference/profiler-heap-object-relationship-flags-enumeration.md) valeurs d’énumération.|  
|PROFILER_HEAP_ENUM_FLAGS_SUBSTRINGS|0x00000002|Cet objet segment de mémoire est utilisé pour afficher la sous-chaîne correctement.|  
|PROFILER_HEAP_ENUM_FLAGS_RELATIONSHIP_SUBSTRINGS|PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS &#124; PROFILER_HEAP_ENUM_FLAGS_SUBSTRINGS|Cet objet segment de mémoire est utilisé pour afficher la sous-chaîne correctement.|