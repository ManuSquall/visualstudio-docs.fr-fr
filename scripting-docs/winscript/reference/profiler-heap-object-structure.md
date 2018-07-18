---
title: Profiler_heap_object, Structure | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 9f35362c-6856-4cfb-b990-031a156a58eb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad50f03806cbf98450c0fc917f1a97ca7305d05c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734339"
---
# <a name="profilerheapobject-structure"></a>PROFILER_HEAP_OBJECT, structure
Représente les objets du tas, regroupés en [iactivescriptprofilercontrol3::enumheap, méthode](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _PROFILER_HEAP_OBJECT  
{  
    UINT size;    union {        PROFILER_HEAP_OBJECT_ID objectId;        PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;    };    PROFILER_HEAP_OBJECT_NAME_ID typeNameId;    USHORT flags;     USHORT optionalInfoCount;} PROFILER_HEAP_OBJECT;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Type|Description|  
|------------|----------|-----------------|  
|objectId|[Type PROFILER_HEAP_OBJECT_ID](../../winscript/reference/profiler-heap-object-id-type.md)|L’ID de l’objet de segment de mémoire.|  
|externalObjectAddress|[Type PROFILER_EXTERNAL_OBJECT_ADDRESS](../../winscript/reference/profiler-external-object-address-type.md)|L’adresse de l’objet externe d’un objet, tel qu’un objet alloué en C++, qui est en dehors du tas JavaScript.|  
|typeNameId|[Type PROFILER_HEAP_OBJECT_NAME_ID](../../winscript/reference/profiler-heap-object-name-id-type.md)|L’ID du nom de type d’objet du tas, extraite [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md). Seul l’un des `externalObjectAddress` ou `typeName` est présent en fonction de la `flags` valeur.|  
|flags|[Énumération PROFILER_HEAP_OBJECT_FLAGS](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Les indicateurs qui contiennent des informations de base sur l’objet de tas.|  
|optionalInfoCount|USHORT|Le nombre de [profiler_heap_object_optional_info, Structure](../../winscript/reference/profiler-heap-object-optional-info-structure.md) enregistrements qui sont disponibles pour l’objet de segment de mémoire.|