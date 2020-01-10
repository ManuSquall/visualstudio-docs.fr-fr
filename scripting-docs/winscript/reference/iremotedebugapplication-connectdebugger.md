---
title: IRemoteDebugApplication::ConnectDebugger | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.ConnectDebugger
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::ConnectDebugger
ms.assetid: ded94101-7efe-466f-aa70-b3e30a38c4d8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ed0ddeffd55475e1be4c9fab1e567d61a4b6654
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572325"
---
# <a name="iremotedebugapplicationconnectdebugger"></a>IRemoteDebugApplication::ConnectDebugger
Connecte un débogueur à cette application.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ConnectDebugger(  
   IApplicationDebugger*  pad  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pad`  
 dans Débogueur à attacher à cette application.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_FAIL`|Un débogueur est déjà connecté à cette application.|  
  
## <a name="remarks"></a>Notes  
 Une application ne peut avoir qu’un seul débogueur connecté à la fois. Cette méthode échoue si un débogueur est déjà connecté.  
  
## <a name="see-also"></a>Voir aussi  
 [IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)   
 [Interface IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)