---
title: 'IRemoteDebugApplicationEvents :: OnConnectDebugger | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: f36199ec50e39daea6e3ec1dcc4f126e1416073b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575630"
---
# <a name="iremotedebugapplicationeventsonconnectdebugger"></a>IRemoteDebugApplicationEvents::OnConnectDebugger
Gère un événement de connexion du débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnConnectDebugger(  
   IApplicationDebugger*  pad  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pad`  
 dans Débogueur qui vient d’être connecté.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode gère l’événement de connexion du débogueur.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md)