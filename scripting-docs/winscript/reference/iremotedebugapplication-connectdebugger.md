---
title: IRemoteDebugApplication::ConnectDebugger | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IRemoteDebugApplication.ConnectDebugger
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::ConnectDebugger
ms.assetid: ded94101-7efe-466f-aa70-b3e30a38c4d8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 538b7a3f76e6026297839e4a7a37e6c21a72d7d0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationconnectdebugger"></a>IRemoteDebugApplication::ConnectDebugger
Se connecte à un débogueur à cette application.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ConnectDebugger(  
   IApplicationDebugger*  pad  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pad`  
 [in] Le débogueur s’attache à cette application.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_FAIL`|Un débogueur est déjà connecté à cette application.|  
  
## <a name="remarks"></a>Remarques  
 Une application peut avoir qu’un seul débogueur connecté à la fois. Cette méthode échoue si un débogueur est déjà connecté.  
  
## <a name="see-also"></a>Voir aussi  
 [IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)   
 [Interface IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)