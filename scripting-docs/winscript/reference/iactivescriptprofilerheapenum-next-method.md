---
title: Iactivescriptprofilerheapenum::Next, méthode | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 0336286f-1dcd-4df9-adf5-76b59b4e74bb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3927743a1de1d3048537327aebd24a847a7d22e5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724589"
---
# <a name="iactivescriptprofilerheapenumnext-method"></a>IActiveScriptProfilerHeapEnum::Next, méthode
Obtient l’objet ou les objets dans l’ensemble des objets du tas à partir de la [iactivescriptprofilercontrol3::enumheap, méthode](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Next (    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] PROFILER_HEAP_OBJECT** heapObjects,     [out] ULONG *pceltFetched);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `celt`  
 Le nombre d’objets à retourner.  
  
 `heapObjects`  
 [out] La prochaine [profiler_heap_object, Structure](../../winscript/reference/profiler-heap-object-structure.md) structures.  
  
 `pceltFetched`  
 [out] Le nombre d’objets renvoyés,  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur HRESULT.