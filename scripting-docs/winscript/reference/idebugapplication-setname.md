---
title: IDebugApplication::SetName | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.SetName
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::SetName
ms.assetid: 7b0ddc58-6f20-4ce3-9bdf-81a6c1d64256
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad54c1c9ba950c7f1b98d393bec2bf65c385ec60
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationsetname"></a>IDebugApplication::SetName
Définit le nom de l’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetName(  
   LPCOLESTR  pstrName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstrName`  
 [in] Le nom de l’application.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Le nom fourni à cette méthode est retourné dans les appels suivants à la `IRemoteDebugApplication::GetName` (méthode).  
  
 Cette méthode doit être appelée avant d’appeler le `IProcessDebugManager::AddApplication` (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugApplication (Interface)](../../winscript/reference/idebugapplication-interface.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)