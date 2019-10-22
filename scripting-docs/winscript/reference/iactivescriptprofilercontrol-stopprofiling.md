---
title: 'IActiveScriptProfilerControl :: StopProfiling | Microsoft Docs'
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
ms.openlocfilehash: da5900678093d57b3c995ac3bca8464ccd612fb2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571542"
---
# <a name="iactivescriptprofilercontrolstopprofiling"></a>IActiveScriptProfilerControl::StopProfiling
Arrête le profilage sur le moteur de script. Cette méthode appelle [IActiveScriptProfilerCallback :: Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) sur l’objet de profileur, puis le libère.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT StopProfiling(  
    [in] HRESULT hrShutdownReason);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `hrShutdownReason`  
 dans HRESULT à passer comme paramètre à la méthode [IActiveScriptProfilerCallback :: Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) de l’objet de profileur.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un HRESULT. Les valeurs possibles sont les suivantes :  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|La méthode a réussi.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Le profilage n’est pas activé.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptProfilerControl](../../winscript/reference/iactivescriptprofilercontrol-interface.md)