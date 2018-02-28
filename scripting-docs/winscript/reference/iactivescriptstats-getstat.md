---
title: IActiveScriptStats::GetStat | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptStats.GetStat
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStat
ms.assetid: 31fd15b3-0713-4b55-b4f7-bfd7ea198493
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35e791661de6d360f747f8d823ad073c2eb81115
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptstatsgetstat"></a>IActiveScriptStats::GetStat
Retourne l’une des statistiques de script standard.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetStat(  
   DWORD   stid,  
   ULONG*  pluHi,  
   ULONG*  pluLo  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `stid`  
 [in] Spécifie les statistiques à retourner. La valeur doit être :  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|SCRIPTSTAT_STATEMENT_COUNT|1|Retourne le nombre d’instructions exécutées depuis le script démarré ou que les statistiques ont été réinitialisées.|  
  
 `pluHi`  
 [out] 32 bits de poids fort d’un entier non signé 64 bits représentant la statistique.  
  
 `pluLo`  
 [out] 32 bits de poids faibles d’un entier non signé 64 bits représentant la statistique.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles incluent, mais ne sont pas limités aux valeurs dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode retourne l’une des statistiques de script standard.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [Interface IActiveScriptStats](../../winscript/reference/iactivescriptstats-interface.md)