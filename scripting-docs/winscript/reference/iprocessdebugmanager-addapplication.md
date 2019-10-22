---
title: 'IProcessDebugManager :: AddApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.AddApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::AddApplication
ms.assetid: 73828299-11eb-4c58-ad70-f80f2d0eede8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47ad8132b9b51efa5f5c2f260e48441e5da64c42
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576810"
---
# <a name="iprocessdebugmanageraddapplication"></a>IProcessDebugManager::AddApplication
Ajoute une application à la liste des applications en cours d’exécution du gestionnaire de débogage d’ordinateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT AddApplication(  
   IDebugApplication*  pda,  
   DWORD*              pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pda`  
 dans Application de débogage à ajouter à la liste des applications en cours d’exécution.  
  
 `pdwAppCookie`  
 à Cookie utilisé pour supprimer l’application du gestionnaire de débogage de l’ordinateur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode ajoute une application à la liste des applications en cours d’exécution dans le gestionnaire de débogage de l’ordinateur.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IProcessDebugManager](../../winscript/reference/iprocessdebugmanager-interface.md)  
 [IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)