---
title: 'IDebugApplication :: SetName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.SetName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::SetName
ms.assetid: 7b0ddc58-6f20-4ce3-9bdf-81a6c1d64256
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a3e5115d4adc3fc3dfa93f10c90cb0d2b36f0e4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571102"
---
# <a name="idebugapplicationsetname"></a>IDebugApplication::SetName
Définit le nom de l’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetName(  
   LPCOLESTR  pstrName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstrName`  
 dans Nom de l’application.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Le nom fourni à cette méthode est retourné dans les appels suivants à la méthode `IRemoteDebugApplication::GetName`.  
  
 Cette méthode doit être appelée avant d’appeler la méthode `IProcessDebugManager::AddApplication`.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)