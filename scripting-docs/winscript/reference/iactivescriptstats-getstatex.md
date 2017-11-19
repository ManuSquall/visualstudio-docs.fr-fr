---
title: IActiveScriptStats::GetStatEx | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptStats.GetStatEx
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptStats::GetStatEx
ms.assetid: f526f51d-8ab5-49ef-a8f7-ae0ac1cb46e4
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cb8adf27811f3046de7b447e537443ef129a8c3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptstatsgetstatex"></a>IActiveScriptStats::GetStatEx
Retourne une statistique de script personnalisé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `guid`  
 [in] Spécifie les statistiques à retourner. La sémantique de celle correspond à un particulier GUID est entièrement moteur défini.  
  
 `pluHi`  
 [out] 32 bits de poids fort d’un entier non signé 64 bits représentant la statistique.  
  
 `pluLo`  
 [out] 32 bits de poids faibles d’un entier non signé 64 bits représentant la statistique.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_NOTIMPL`|La méthode n’est pas implémentée.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode permet à un moteur de script personnalisé retourner des statistiques significatives pour un hôte personnalisé.  
  
> [!NOTE]
>  Cette méthode n’est pas implémentée actuellement.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)   
 [Interface IActiveScriptStats](../../winscript/reference/iactivescriptstats-interface.md)