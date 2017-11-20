---
title: "Profiler_heap_object_flags, énumération | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 17936b7a-40d5-4774-b92b-b24ee391591e
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2a7a27f4d9d7f834b07a2db5ba8433b63222a3b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="profilerheapenumflags-enumeration"></a>PROFILER_HEAP_OBJECT_FLAGS, énumération
Indicateurs qui représentent des si des informations supplémentaires sur un objet de tas pointé dans une relation d’objet sont exposées. Utilisé dans le [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef [v1_enum] enum {    PROFILER_HEAP_ENUM_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS  = 0x00000001,} PROFILER_HEAP_ENUM_FLAGS;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Valeur|Description|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_ENUM_FLAGS_NONE|0x00000000|Cet objet de segment de mémoire n’expose pas d’informations supplémentaires sur une relation d’objet. Cet objet de segment de mémoire se comporte de la même façon que [IActiveScriptProfilerControl3::HeapEnum](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|PROFILER_HEAP_ENUM_ENUM_ STORE_RELATIONSHIP_FLAGS|0x00000001|Cet objet de tas exposera plus d’informations sur un objet dans une relation d’objet vers lequel pointé soit ou non une méthode d’accesseur Get ou Set. Ces informations sont stockées dans les 2 octets (16 bits) haute de la [PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) champ comme l’un de le [PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS](../../winscript/reference/profiler-heap-object-relationship-flags-enumeration.md) valeurs d’énumération.|  
|PROFILER_HEAP_ENUM_FLAGS_SUBSTRINGS|0x00000002|Cet objet de segment de mémoire est utilisé pour afficher la sous-chaîne correctement.|  
|PROFILER_HEAP_ENUM_FLAGS_RELATIONSHIP_SUBSTRINGS|PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS &#124; PROFILER_HEAP_ENUM_FLAGS_SUBSTRINGS|Cet objet de segment de mémoire est utilisé pour afficher la sous-chaîne correctement.|