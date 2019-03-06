---
title: ISimpleConnectionPoint::Unadvise | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 83fdf8f6a6e9378d328a9df61b1561a1ae747ae8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089261"
---
# <a name="isimpleconnectionpointunadvise"></a>ISimpleConnectionPoint::Unadvise
Met fin à une connexion de notifications précédemment établie par `ISimpleConnectionPoint::Advise`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Unadvise(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwCookie`  
 [in] Jeton de la connexion à terminer, tel que retourné par `ISimpleConnectionPoint::Advise`.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Une fois une connexion de notifications est terminée, le point de connexion appelle le `Release` méthode sur le pointeur qui a été enregistré pour la connexion au cours de la `ISimpleConnectionPoint::Advise` (méthode). Qui appellent inverse la `AddRef` qui a été effectuée pendant la `ISimpleConnectionPoint::Advise` lorsque le point de connexion appelle le récepteur de notifications `QueryInterface`.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)