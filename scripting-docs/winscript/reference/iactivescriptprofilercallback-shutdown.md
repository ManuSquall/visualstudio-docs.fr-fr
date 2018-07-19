---
title: IActiveScriptProfilerCallback::Shutdown | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: ec47cd5f581c36abb60b662983c6d806a4732f47
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724729"
---
# <a name="iactivescriptprofilercallbackshutdown"></a>IActiveScriptProfilerCallback::Shutdown
Appelé pour informer l’objet de profileur chaque fois que le profilage est arrêté sur un moteur de script. De cette manière, l’objet de profileur peut appeler des routines de son nettoyage, si nécessaire. Cette méthode est également appelée par le moteur de script lorsque le moteur de script s’arrête ou lorsqu’un appel à [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) échoue.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `hrReason`  
 [in] Raison de l’arrêt. Si le moteur de script en cours d’arrêt, `S_OK` est passé. Si l’appel à [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) retourne un HRESULT d’échec, la valeur HRESULT est passée. Sinon, cette valeur est extraite de [IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md).  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur de retour de cette méthode est ignorée par le moteur de script.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)