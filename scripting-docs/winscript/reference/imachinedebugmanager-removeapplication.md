---
title: 'IMachineDebugManager :: RemoveApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManager.RemoveApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManager::RemoveApplication
ms.assetid: 873509ce-e638-484a-b2a2-489a8ce7dbfe
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87951e55a7cfcfef1a366f79c380948c7651ed12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573935"
---
# <a name="imachinedebugmanagerremoveapplication"></a>IMachineDebugManager::RemoveApplication
Supprime une application de la liste des applications en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT RemoveApplication(  
   DWORD  dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwAppCookie`  
 dans Cookie fourni lorsque l’application a été ajoutée à la liste des applications.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode est appelée par le gestionnaire de débogage de processus chaque fois que `IProcessDebugManager::RemoveApplication` est appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [IMachineDebugManager :: AddApplication](../../winscript/reference/imachinedebugmanager-addapplication.md)    
 @No__t_1 de l' [interface IMachineDebugManager](../../winscript/reference/imachinedebugmanager-interface.md)  
 [IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)