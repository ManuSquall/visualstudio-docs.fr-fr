---
title: 'ISimpleConnectionPoint :: Unadvise | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Unadvise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Unadvise
ms.assetid: eae06a58-ed42-4839-aad4-14420b15343f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e00c172fd33eb0ccf27aaf28e0e2f692c1a353ab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571750"
---
# <a name="isimpleconnectionpointunadvise"></a>ISimpleConnectionPoint::Unadvise
Met fin à une connexion de notifications précédemment établie par le biais de `ISimpleConnectionPoint::Advise`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Unadvise(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwCookie`  
 dans Jeton de la connexion à terminer, tel que retourné par `ISimpleConnectionPoint::Advise`.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Lorsqu’une connexion consultative est terminée, le point de connexion appelle la méthode `Release` sur le pointeur qui a été enregistré pour la connexion pendant la méthode `ISimpleConnectionPoint::Advise`. Cet appel inverse le `AddRef` qui a été effectué lors de l' `ISimpleConnectionPoint::Advise` lorsque le point de connexion appelle le `QueryInterface` du récepteur de notifications.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)