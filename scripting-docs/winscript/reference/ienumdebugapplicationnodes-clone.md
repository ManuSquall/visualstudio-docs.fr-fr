---
title: IEnumDebugApplicationNodes::Clone | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumDebugApplicationNodes.Clone
apilocation: pdm.dll
helpviewer_keywords: IEnumDebugApplicationNodes::Clone
ms.assetid: 7190954d-e2da-4a84-8e37-81d4d27886a8
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dab58a36110c0f0321bbf490a105bff9cddad009
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugapplicationnodesclone"></a>IEnumDebugApplicationNodes::Clone
Crée un énumérateur qui contient le même état que l’énumérateur actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Clone(  
   IEnumDebugApplicationNodes**  pperddp  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pperddp`  
 [out] Retourne le `IEnumDebugApplicationNodes` interface du clone de l’énumérateur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode crée un énumérateur qui contient le même état que l’énumérateur actuel.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IEnumDebugApplicationNodes](../../winscript/reference/ienumdebugapplicationnodes-interface.md)