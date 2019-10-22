---
title: 'IEnumRemoteDebugApplications :: suivant | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumRemoteDebugApplications.Next
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumRemoteDebugApplications::Next
ms.assetid: 33f6c620-6dd3-4057-b982-b88a7a1f02b4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a9ebcbbd786ba8545e19b9833d26e5e385738c4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575216"
---
# <a name="ienumremotedebugapplicationsnext"></a>IEnumRemoteDebugApplications::Next
La méthode `Next` récupère un nombre spécifié de segments dans la séquence d’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Next(  
   ULONG                      celt,  
   IRemoteDebugApplication**  ppda,  
   ULONG*                     pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `celt`  
 dans Nombre de segments à récupérer.  
  
 `ppda`  
 à Retourne un tableau d’interfaces `IRemoteDebugApplication` qui représente les segments récupérés.  
  
 `pceltFetched`  
 à Nombre réel de segments récupérés par l’énumérateur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode récupère un nombre spécifié de segments dans la séquence d’énumération.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IEnumRemoteDebugApplications](../../winscript/reference/ienumremotedebugapplications-interface.md)