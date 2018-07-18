---
title: IRemoteDebugApplicationEvents::OnConnectDebugger | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEvents.OnConnectDebugger
apilocation:
- jscript.dll
helpviewer_keywords:
- IRemoteDebugApplicationEvents::OnConnectDebugger
ms.assetid: 8c9c19b8-5426-4643-83e6-b68803ff69c4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 66ea40164dee8b4f7b82166ebc23abe1bc254226
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728849"
---
# <a name="iremotedebugapplicationeventsonconnectdebugger"></a>IRemoteDebugApplicationEvents::OnConnectDebugger
Gère un débogueur connecter l’événement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OnConnectDebugger(  
   IApplicationDebugger*  pad  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pad`  
 [in] Le débogueur qui vient d’être connecté.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode le débogueur gère les événements de connexion.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md)