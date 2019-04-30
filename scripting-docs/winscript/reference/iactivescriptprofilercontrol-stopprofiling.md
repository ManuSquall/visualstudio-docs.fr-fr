---
title: IActiveScriptProfilerControl::StopProfiling | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.StopProfiling
apilocation:
- scrobj.dll
ms.assetid: 23b46ed6-a398-44c0-bc49-bf122e697cfe
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 750693db9aa809e6b3521f0312cebcf45d8d720d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993006"
---
# <a name="iactivescriptprofilercontrolstopprofiling"></a>IActiveScriptProfilerControl::StopProfiling
Arrête le profilage sur le moteur de script. Cette méthode appelle [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) sur l’objet de profileur, puis le libère.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT StopProfiling(  
    [in] HRESULT hrShutdownReason);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `hrShutdownReason`  
 [in] La valeur HRESULT devant être passée comme paramètre à la [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) méthode de l’objet de profileur.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une valeur HRESULT. Les valeurs possibles sont les suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|La méthode a réussi.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profilage n’est pas activé.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptProfilerControl](../../winscript/reference/iactivescriptprofilercontrol-interface.md)