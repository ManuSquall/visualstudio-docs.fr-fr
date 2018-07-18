---
title: IProcessDebugManager::AddApplication | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: a221aa0038b0b3fd5046b9ada08e2de86f33a895
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729519"
---
# <a name="iprocessdebugmanageraddapplication"></a>IProcessDebugManager::AddApplication
Ajoute une application sur la machine debug liste du Gestionnaire d’applications en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT AddApplication(  
   IDebugApplication*  pda,  
   DWORD*              pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pda`  
 [in] Application de débogage à ajouter à la liste des applications en cours d’exécution.  
  
 `pdwAppCookie`  
 [out] Un cookie est utilisé pour supprimer l’application à partir du Gestionnaire de débogage d’ordinateur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode ajoute une application en cours d’exécution la liste des applications dans le Gestionnaire de débogage d’ordinateur.  
  
## <a name="see-also"></a>Voir aussi  
 [IProcessDebugManager (Interface)](../../winscript/reference/iprocessdebugmanager-interface.md)   
 [IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)