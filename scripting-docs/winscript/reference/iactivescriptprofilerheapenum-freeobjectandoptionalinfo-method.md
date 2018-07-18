---
title: Iactivescriptprofilerheapenum::freeobjectandoptionalinfo, méthode | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fdd5f7cc-be4e-4c13-a181-6320d26b44eb
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 748e5dbc948cc22e084a4e0b1e13222174bb739e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724469"
---
# <a name="iactivescriptprofilerheapenumfreeobjectandoptionalinfo-method"></a>IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo, méthode
Libère spécifié [profiler_heap_object, Structure](../../winscript/reference/profiler-heap-object-structure.md) leur sont associées et des structures [profiler_heap_object_optional_info, Structure](../../winscript/reference/profiler-heap-object-optional-info-structure.md) éléments.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT FreeObjectAndOptionalInfo (    [in] ULONG celt,    [in, size_is(celt)] PROFILER_HEAP_OBJECT** heapObjects);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `celt`  
 Le nombre d’objets à libérer.  
  
 `heapObjects`  
 Un tableau de [profiler_heap_object, Structure](../../winscript/reference/profiler-heap-object-structure.md) structures.  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur HRESULT.