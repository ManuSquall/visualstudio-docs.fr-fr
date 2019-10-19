---
title: 'IActiveScriptProfilerControl :: StartProfiling | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.StartProfiling
apilocation:
- scrobj.dll
ms.assetid: 56a7b3b7-8c21-43d0-9d8b-53bbc19fabb9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cfc59dd43ac3eed433f92af2cdd0aefe40392c4a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571568"
---
# <a name="iactivescriptprofilercontrolstartprofiling"></a>IActiveScriptProfilerControl::StartProfiling
Démarre le profilage sur le moteur de script. Le moteur de script crée une instance de l’objet de profileur en appelant [CoCreateInstance](https://docs.microsoft.com/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT StartProfiling(  
    [in] REFCLSID clsidProfilerObject,  
    [in] DWORD dwEventMask,  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `clsidProfilerObject`  
 dans Identificateur de classe (CLSID) de l’objet de profileur à créer.  
  
 `dwEventMask`  
 dans Masque de bits de 4 octets qui spécifie les types d’événements. Les bits sont définis dans l' [énumération PROFILER_EVENT_MASK](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
 `dwContext`  
 dans Valeur de 4 octets qui est passée à l’objet de profileur.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un HRESULT. Les valeurs possibles sont les suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|La méthode a réussi.|  
|`ACTIVPROF_E_PROFILER_PRESENT`|Le profilage est déjà activé.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptProfilerControl](../../winscript/reference/iactivescriptprofilercontrol-interface.md)