---
title: "Iactivescriptprofilercontrol5::enumheap2, méthode | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a25859eb-ac28-4a97-bcb3-33788982a76b
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c493acdb2843877c506d9d84e145a79ac2d60d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrol5enumheap2-method"></a>IActiveScriptProfilerControl5::EnumHeap2, méthode
Retourne une interface ([iactivescriptprofilerheapenum, Interface](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) qui peut être utilisé pour itérer sur les objets du tas GC dans le contexte du moteur de script associé.  
  
 Vous pouvez appeler cette méthode dans un débogage ou en mode version finale. Cette méthode doit être appelée lorsque le thread d’interface utilisateur est inactif. Une fois que la méthode a été appelée, aucune opération ne doit être effectuée dans le moteur de script à l’exception de [iactivescriptprofilerheapenum::Next, méthode](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) jusqu'à ce que [iactivescriptprofilerheapenum::Next, méthode](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)retourne S_FALSE ou [iactivescriptprofilerheapenum, Interface](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) pointeur d’interface est libéré.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumHeap2(    [in] PROFILER_HEAP_ENUM_FLAGS enumFlags,    [out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>Paramètres  
 enumFlags  
 Valeur qui spécifie si des informations supplémentaires sur un objet vers lequel pointé dans une relation d’objet sont exposées. Informations supplémentaires peuvent indiquer si l’objet désigné est une méthode d’accesseur Get ou Set. Pour plus d’informations, consultez [profiler_heap_object_flags, énumération](../../winscript/reference/profiler-heap-enum-flags-enumeration.md).  
  
 ppEnum  
 [out] Retourne le [iactivescriptprofilerheapenum, Interface](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une valeur HRESULT. Les valeurs possibles sont les suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|L’énumération de segment de mémoire s’est terminée correctement.|  
|`E_OUTOFMEMORY`|Il n’a pas assez de mémoire disponible pour effectuer l’énumération de tas.|  
|`E_FAIL`|Une erreur interne s’est produite.|