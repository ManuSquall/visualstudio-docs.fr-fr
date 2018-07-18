---
title: IRemoteDebugApplicationEvents::OnLeaveBreakPoint | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 9afb48ceca742ef736dd8f79ba8c3d96e3a56a82
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728709"
---
# <a name="iremotedebugapplicationeventsonleavebreakpoint"></a>IRemoteDebugApplicationEvents::OnLeaveBreakPoint
Gère un événement de conserver un point d’arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OnLeaveBreakPoint(  
   IRemoteDebugApplicationThread*  prdat  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `prdat`  
 [in] Le thread d’application qui ont quitté le point d’arrêt.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode gère un événement de conserver un point d’arrêt.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md)