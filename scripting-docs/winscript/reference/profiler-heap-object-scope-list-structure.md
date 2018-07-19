---
title: Profiler_heap_object_scope_list, Structure | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 33ebaa31-0a35-47d5-a4e3-afd83e16f53e
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67f0972faee11e15bd5d0e9a219e439df49d9672
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734259"
---
# <a name="profilerheapobjectscopelist-structure"></a>PROFILER_HEAP_OBJECT_SCOPE_LIST, structure
Cette structure est associée aux objets de fonction uniquement. La liste de l’étendue représente la fermeture de la fonction sous la forme d’une liste d’étendues, où chaque étendue est un objet de segment de mémoire avec une liste de propriétés associée qui représente les variables dans chaque étendue donnée. Dans certains cas, les noms des objets qu’étendue ne peut pas être disponible et seulement leur index dans la liste de propriétés est disponible.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_SCOPE_LIST{    UINT count;    [size_is(count)] PROFILER_HEAP_OBJECT_ID scopes[];} PROFILER_HEAP_OBJECT_SCOPE_LIST;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Type|Description|  
|------------|----------|-----------------|  
|count|UINT|Le nombre d’étendues|  
|scopes|[Type PROFILER_HEAP_OBJECT_ID](../../winscript/reference/profiler-heap-object-id-type.md)|Un tableau d’étendues.|