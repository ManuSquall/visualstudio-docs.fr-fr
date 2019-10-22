---
title: 'IEnumDebugApplicationNodes :: suivant | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugApplicationNodes.Next
apilocation:
- pdm.dll
helpviewer_keywords:
- IEnumDebugApplicationNodes::Next
ms.assetid: 925511c8-4f11-423d-ba2d-01589457050c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4ad47c0119eb46c05368fa40ba3a5965fecce0b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573054"
---
# <a name="ienumdebugapplicationnodesnext"></a>IEnumDebugApplicationNodes::Next
Récupère un nombre spécifié de segments dans la séquence d’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Next(  
   ULONG                    celt,  
   IDebugApplicationNode**  pprddp,  
   ULONG*                   pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `celt`  
 dans Nombre de segments à récupérer.  
  
 `pprddp`  
 à Retourne un tableau d’interfaces `IDebugApplicationNode` qui représente les segments récupérés.  
  
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
 [Interface IEnumDebugApplicationNodes](../../winscript/reference/ienumdebugapplicationnodes-interface.md)