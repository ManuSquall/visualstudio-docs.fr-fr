---
title: 'IRemoteDebugApplicationEvents :: OnLeaveBreakPoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEvents.OnLeaveBreakPoint
apilocation:
- jscript.dll
helpviewer_keywords:
- IRemoteDebugApplicationEvents::OnLeaveBreakPoint
ms.assetid: 00449a23-1f67-4078-ad06-4c426abf7587
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1f4be875f5b420ff96e22ee06cdbeb2929466381
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571950"
---
# <a name="iremotedebugapplicationeventsonleavebreakpoint"></a>IRemoteDebugApplicationEvents::OnLeaveBreakPoint
Gère un événement pour quitter un point d’arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnLeaveBreakPoint(  
   IRemoteDebugApplicationThread*  prdat  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `prdat`  
 dans Thread d’application qui a quitté le point d’arrêt.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode gère un événement pour quitter un point d’arrêt.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md)