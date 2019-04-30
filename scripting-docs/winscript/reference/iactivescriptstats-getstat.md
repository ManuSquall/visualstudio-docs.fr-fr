---
title: IActiveScriptStats::GetStat | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStat
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStat
ms.assetid: 31fd15b3-0713-4b55-b4f7-bfd7ea198493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8befb3da4e4b6f060a5f58aedec3604afe70aefb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992016"
---
# <a name="iactivescriptstatsgetstat"></a>IActiveScriptStats::GetStat
Retourne une des statistiques de script standard.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetStat(  
   DWORD   stid,  
   ULONG*  pluHi,  
   ULONG*  pluLo  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `stid`  
 [in] Spécifie les statistiques à retourner. La valeur doit être :  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|SCRIPTSTAT_STATEMENT_COUNT|1|Retourne le nombre d’instructions exécutées depuis le script démarré ou que les statistiques ont été réinitialisées.|  
  
 `pluHi`  
 [out] 32 bits de poids fort d’un entier non signé 64 bits représentant la statistique.  
  
 `pluLo`  
 [out] 32 bits de poids faibles d’un entier non signé 64 bits représentant la statistique.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles incluent, mais ne sont pas limitées aux valeurs dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne une des statistiques de script standard.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [Interface IActiveScriptStats](../../winscript/reference/iactivescriptstats-interface.md)