---
title: 'IActiveScriptProfilerControl :: SetProfilerEventMask | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.SetProfilerEventMask
apilocation:
- scrobj.dll
ms.assetid: 207e192f-e12e-4fcb-b4d8-eaee50ecb86e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4162cf2e5325bfb41bce9c3a47a52b1b36d74f2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571578"
---
# <a name="iactivescriptprofilercontrolsetprofilereventmask"></a>IActiveScriptProfilerControl::SetProfilerEventMask
Définit un masque de bits de 4 octets qui spécifie les types d’événements que le moteur de script doit déclencher.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetProfilerEventMask(  
    [in] DWORD dwEventMask);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwEventMask`  
 dans Masque de bits de 4 octets qui spécifie les types d’événements. Les bits sont définis dans l' [énumération PROFILER_EVENT_MASK](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un HRESULT. Les valeurs possibles sont les suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|La méthode a réussi.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Le profilage n’est pas activé.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptProfilerControl](../../winscript/reference/iactivescriptprofilercontrol-interface.md)