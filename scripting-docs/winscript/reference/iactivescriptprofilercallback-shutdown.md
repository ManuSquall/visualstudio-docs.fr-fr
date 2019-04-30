---
title: IActiveScriptProfilerCallback::Shutdown | Microsoft Docs
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
ms.openlocfilehash: 091ccc30f16081fdca8f10778efec208ef5ccb16
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993421"
---
# <a name="iactivescriptprofilercallbackshutdown"></a>IActiveScriptProfilerCallback::Shutdown
Appelé pour informer l’objet de profileur chaque fois que le profilage est arrêté sur un moteur de script. De cette façon, l’objet de profileur peut appeler des routines de son nettoyage, si nécessaire. Cette méthode est également appelée par le moteur de script lorsque le moteur de script s’arrête, ou lorsqu’un appel à [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) échoue.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `hrReason`  
 [in] Raison de l’arrêt. Si le moteur de script s’arrête, `S_OK` est passé. Si l’appel à [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) retourne un HRESULT d’échec, le HRESULT est passé. Sinon, cette valeur est extraite de [IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md).  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur de retour de cette méthode est ignorée par le moteur de script.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)