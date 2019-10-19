---
title: 'ISimpleConnectionPoint :: Advise | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Advise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Advise
ms.assetid: 59ded60d-b938-4110-aca3-e69ba234ca9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7d08d4774dffbfd840c674b15abe82bedb37e5f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571825"
---
# <a name="isimpleconnectionpointadvise"></a>ISimpleConnectionPoint::Advise
Établit une connexion entre l’objet de point de connexion simple et le récepteur du client.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdisp`  
 dans Pointeur vers l’interface `IDispatch` sur le récepteur de notification du client. Le récepteur du client reçoit les appels sortants du point de connexion simple.  
  
 `pdwCookie`  
 à Pointeur vers un jeton retourné qui identifie de façon unique cette connexion. L’appelant utilise ce jeton ultérieurement pour supprimer la connexion en le passant à la méthode `ISimpleConnectionPoint::Unadvise`. Si la connexion n’a pas été établie, cette valeur est égale à zéro.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode établit une connexion entre l’objet de point de connexion simple et le récepteur du client.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)  
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)