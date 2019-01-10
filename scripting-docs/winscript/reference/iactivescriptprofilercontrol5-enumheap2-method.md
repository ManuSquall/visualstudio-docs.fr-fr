---
title: Méthode IActiveScriptProfilerControl5::EnumHeap2 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a25859eb-ac28-4a97-bcb3-33788982a76b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 21661953edbdba2314b88aad5fb55451b06b51a8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097628"
---
# <a name="iactivescriptprofilercontrol5enumheap2-method"></a>IActiveScriptProfilerControl5::EnumHeap2, méthode
Retourne une interface ([iactivescriptprofilerheapenum, Interface](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) qui peut être utilisé pour itérer sur les objets du tas de garbage collection dans le contexte du moteur de script associé.  
  
 Vous pouvez appeler cette méthode dans debug ou en mode version finale. Cette méthode doit être appelée lorsque le thread d’interface utilisateur est inactif. Une fois que la méthode a été appelée, aucune opération ne doit être effectuée sur le moteur de script à l’exception [méthode IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) jusqu'à ce que [méthode IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)retourne S_FALSE ou [iactivescriptprofilerheapenum, Interface](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) interface pointeur est relâché.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT EnumHeap2(    [in] PROFILER_HEAP_ENUM_FLAGS enumFlags,    [out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>Paramètres  
 enumFlags  
 Valeur qui spécifie si des informations supplémentaires sur un objet désigné dans une relation entre objets sont exposées. Informations supplémentaire peuvent indiquer si l’objet pointé est une méthode getter ou setter. Pour plus d’informations, consultez [profiler_heap_object_flags, énumération](../../winscript/reference/profiler-heap-enum-flags-enumeration.md).  
  
 ppEnum  
 [out] Retourne le [iactivescriptprofilerheapenum, Interface](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une valeur HRESULT. Les valeurs possibles sont les suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|L’énumération de segment de mémoire s’est terminée correctement.|  
|`E_OUTOFMEMORY`|Il n’a pas suffisamment de mémoire disponible pour effectuer l’énumération de tas.|  
|`E_FAIL`|Une erreur interne s’est produite.|