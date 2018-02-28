---
title: IRemoteDebugApplication::EnumThreads | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IRemoteDebugApplication.EnumThreads
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::EnumThreads
ms.assetid: b4d7294c-1f15-4f7e-bdfd-700e3bf98cea
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 42b57e63716804258ba79ed4e4aceae118cb5f54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationenumthreads"></a>IRemoteDebugApplication::EnumThreads
Énumère tous les threads connus pour être associé à l’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumThreads(  
   IEnumRemoteDebugApplicationThreads**  pperdat  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pperdat`  
 [out] Énumérateur qui répertorie tous les threads connus pour être associé à l’application.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode énumère tous les threads connus pour être associé à l’application. Nouveaux threads peuvent être ajoutés à tout moment.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)