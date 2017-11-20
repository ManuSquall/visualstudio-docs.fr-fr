---
title: IActiveScriptProfilerControl::SetProfilerEventMask | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProfilerControl.SetProfilerEventMask
apilocation: scrobj.dll
ms.assetid: 207e192f-e12e-4fcb-b4d8-eaee50ecb86e
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b20b5410af7e48f1b9dadb937e794c1941e74df
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilercontrolsetprofilereventmask"></a>IActiveScriptProfilerControl::SetProfilerEventMask
Définit un masque de bits de 4 octets qui spécifie les types d’événements le moteur de script doit déclencher.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
RESULT SetProfilerEventMask(  
    [in] DWORD dwEventMask);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwEventMask`  
 [in] Masque de bits sur 4 octets qui spécifie les types d’événements. Les bits sont définis dans [profiler_event_mask, énumération](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une valeur HRESULT. Les valeurs possibles sont les suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|La méthode a réussi.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profilage n’est pas activé.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptProfilerControl](../../winscript/reference/iactivescriptprofilercontrol-interface.md)