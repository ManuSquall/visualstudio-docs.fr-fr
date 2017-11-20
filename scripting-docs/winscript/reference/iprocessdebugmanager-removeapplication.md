---
title: IProcessDebugManager::RemoveApplication | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IProcessDebugManager.RemoveApplication
apilocation: pdm.dll
helpviewer_keywords: IProcessDebugManager::RemoveApplication
ms.assetid: 334e869d-81ae-4d30-9e89-89763ad4f184
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b8d95be6227f192596e174095744a4e0247e0c37
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iprocessdebugmanagerremoveapplication"></a>IProcessDebugManager::RemoveApplication
Supprime une application en cours d’exécution la liste des applications.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RemoveApplication(  
   DWORD  dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwAppCookie`  
 [in] Cookie fourni par `IProcessDebugManager::AddApplication` lorsque l’application a été ajoutée à la liste des applications.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode supprime une application à partir de l’exécution liste des applications.  
  
## <a name="see-also"></a>Voir aussi  
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)   
 [Interface IProcessDebugManager](../../winscript/reference/iprocessdebugmanager-interface.md)