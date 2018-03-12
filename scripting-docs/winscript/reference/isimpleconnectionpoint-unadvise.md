---
title: ISimpleConnectionPoint::Unadvise | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Unadvise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Unadvise
ms.assetid: eae06a58-ed42-4839-aad4-14420b15343f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7f926f206bb8a27e6265fd147909a5adb13c3543
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="isimpleconnectionpointunadvise"></a>ISimpleConnectionPoint::Unadvise
Met fin à une connexion de notifications précédemment établie par `ISimpleConnectionPoint::Advise`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Unadvise(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwCookie`  
 [in] Jeton de la connexion à terminer, tel que retourné par `ISimpleConnectionPoint::Advise`.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Une fois une connexion de notifications est terminée, le point de connexion appelle la `Release` méthode sur le pointeur a été enregistré pour la connexion au cours de la `ISimpleConnectionPoint::Advise` (méthode). Qui appellent inverse la `AddRef` qui a été effectuée au cours de la `ISimpleConnectionPoint::Advise` lorsque le point de connexion appelle le récepteur de notifications `QueryInterface`.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)