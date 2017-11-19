---
title: IMachineDebugManager::RemoveApplication | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IMachineDebugManager.RemoveApplication
apilocation: scrobj.dll
helpviewer_keywords: IMachineDebugManager::RemoveApplication
ms.assetid: 873509ce-e638-484a-b2a2-489a8ce7dbfe
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6ee371ded11f38b5e049e236c92292d6f662f525
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="imachinedebugmanagerremoveapplication"></a>IMachineDebugManager::RemoveApplication
Supprime une application en cours d’exécution la liste des applications.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RemoveApplication(  
   DWORD  dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwAppCookie`  
 [in] Le cookie fourni lors de l’application a été ajoutée à la liste des applications.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode est appelée par le Gestionnaire de processus de débogage chaque fois que `IProcessDebugManager::RemoveApplication` est appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [IMachineDebugManager::AddApplication](../../winscript/reference/imachinedebugmanager-addapplication.md)   
 [IMachineDebugManager (Interface)](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)