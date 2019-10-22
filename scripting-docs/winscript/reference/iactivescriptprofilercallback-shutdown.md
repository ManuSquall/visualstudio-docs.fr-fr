---
title: 'IActiveScriptProfilerCallback :: Shutdown | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.Shutdown
apilocation:
- scrobj.dll
ms.assetid: 1281bf3c-d7d8-4ff5-9d8a-d1761fdb262e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: deecfe4134a4b0e18591823f194ceaf6d1eb0a14
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571649"
---
# <a name="iactivescriptprofilercallbackshutdown"></a>IActiveScriptProfilerCallback::Shutdown
Appelé pour informer l’objet de profileur quand le profilage est arrêté sur un moteur de script. De cette façon, l’objet de profileur peut appeler ses routines de nettoyage, si nécessaire. Cette méthode est également appelée par le moteur de script lorsque le moteur de script est en cours d’arrêt ou lorsqu’un appel à [IActiveScriptProfilerCallback :: Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) échoue.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `hrReason`  
 dans Raison de l’arrêt. Si le moteur de script est en cours d’arrêt, `S_OK` est passé. Si l’appel à [IActiveScriptProfilerCallback :: Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) retourne un HRESULT d’échec, HRESULT est passé. Sinon, cette valeur est récupérée à partir de [IActiveScriptProfilerControl :: StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md).  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur de retour de cette méthode est ignorée par le moteur de script.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)