---
title: ISimpleConnectionPoint::Advise | Microsoft Docs
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
ms.openlocfilehash: 98db9c92f682808ce8ecc9f6aa382a2eb2bd8495
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153108"
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
 [in] Pointeur vers le `IDispatch` le récepteur de notifications de l’interface sur le client. Récepteur du client reçoit les appels sortants à partir du point de connexion simple.  
  
 `pdwCookie`  
 [out] Pointeur vers un jeton retourné qui identifie de façon unique cette connexion. L’appelant utilise ultérieurement ce jeton pour supprimer la connexion en le passant à la `ISimpleConnectionPoint::Unadvise` (méthode). Si la connexion n’a pas été établie, cette valeur est zéro.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode établit une connexion entre l’objet de point de connexion simple et le récepteur du client.  
  
## <a name="see-also"></a>Voir aussi  
 [ISimpleConnectionPoint (Interface)](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)