---
title: 'IEnumDebugApplicationNodes :: Clone | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugApplicationNodes.Clone
apilocation:
- pdm.dll
helpviewer_keywords:
- IEnumDebugApplicationNodes::Clone
ms.assetid: 7190954d-e2da-4a84-8e37-81d4d27886a8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1d5488f260784450d2b7695972c78a5f9271eed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573062"
---
# <a name="ienumdebugapplicationnodesclone"></a>IEnumDebugApplicationNodes::Clone
Crée un énumérateur qui contient le même État que l’énumérateur actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Clone(  
   IEnumDebugApplicationNodes**  pperddp  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pperddp`  
 à Retourne l’interface `IEnumDebugApplicationNodes` du clone de l’énumérateur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode crée un énumérateur qui contient le même État que l’énumérateur actuel.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IEnumDebugApplicationNodes](../../winscript/reference/ienumdebugapplicationnodes-interface.md)