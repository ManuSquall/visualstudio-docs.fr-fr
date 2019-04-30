---
title: Méthode IActiveScriptProfilerHeapEnum::GetOptionalInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 99ed9df5-71cf-4c25-b189-af9accc466ee
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab8096b79cfbb91e4b65256c84ab1ba01207d9ed
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992838"
---
# <a name="iactivescriptprofilerheapenumgetoptionalinfo-method"></a>IActiveScriptProfilerHeapEnum::GetOptionalInfo, méthode
Obtient des informations facultatives sur l’objet spécifié (à partir de l’ensemble des objets du tas retourné à partir de la [iactivescriptprofilercontrol3::enumheap, méthode](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)).  
  
 Vous ne devez pas libérer la mémoire retournée affectée pour les objets retournés. Au lieu de cela, vous devez appeler la [iactivescriptprofilerheapenum::freeobjectandoptionalinfo, méthode](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetOptionalInfo (    [in] PROFILER_HEAP_OBJECT* heapObject,    [in] ULONG celt,    [out, size_is(celt)] PROFILER_HEAP_OBJECT_OPTIONAL_INFO* optionalInfo);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `heapObject`  
 Le [profiler_heap_object, Structure](../../winscript/reference/profiler-heap-object-structure.md) pour lequel retourner les informations.  
  
 `celt`  
 Le nombre de [profiler_heap_object_optional_info, Structure](../../winscript/reference/profiler-heap-object-optional-info-structure.md) structures à retourner.  
  
 `optionalInfo`  
 [out] Un tableau de [profiler_heap_object_optional_info, Structure](../../winscript/reference/profiler-heap-object-optional-info-structure.md) structures pour l’objet spécifié.  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur HRESULT.