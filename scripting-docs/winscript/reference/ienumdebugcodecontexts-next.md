---
title: IEnumDebugCodeContexts::Next | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumDebugCodeContexts.Next
apilocation: jscript.dll
helpviewer_keywords: IEnumDebugCodeContexts::Next
ms.assetid: 844cc353-ae0b-45e1-84a6-32b0bb67f57f
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 00a3a5765f5b5a62753653d24cf27e4667a5647f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugcodecontextsnext"></a>IEnumDebugCodeContexts::Next
Récupère un nombre spécifié de segments dans la séquence d’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Next(  
   ULONG                celt,  
   IDebugCodeContext**  pscc,  
   ULONG*               pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `celt`  
 [in] Le nombre de segments à récupérer.  
  
 `pscc`  
 [out] Retourne un tableau de `IDebugCodeContext` les interfaces qui représente les segments en cours de récupération.  
  
 `pceltFetched`  
 [out] Le nombre réel de segments lues par l’énumérateur.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode récupère un nombre spécifié de segments dans la séquence d’énumération.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IEnumDebugCodeContexts](../../winscript/reference/ienumdebugcodecontexts-interface.md)