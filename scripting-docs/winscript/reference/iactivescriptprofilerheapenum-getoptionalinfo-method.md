---
title: Iactivescriptprofilerheapenum::getoptionalinfo, méthode | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 99ed9df5-71cf-4c25-b189-af9accc466ee
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6ad237f2feb173408e895984dab7e7455004d16
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724679"
---
# <a name="iactivescriptprofilerheapenumgetoptionalinfo-method"></a>IActiveScriptProfilerHeapEnum::GetOptionalInfo, méthode
Obtient des informations facultatives sur l’objet spécifié (à partir de l’ensemble des objets du tas retournée à partir de la [iactivescriptprofilercontrol3::enumheap, méthode](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)).  
  
 Vous ne devez pas libérer la mémoire retournée est affectée aux objets retournés. Au lieu de cela, vous devez appeler la [iactivescriptprofilerheapenum::freeobjectandoptionalinfo, méthode](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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