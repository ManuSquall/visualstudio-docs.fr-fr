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
ms.openlocfilehash: 096f1cf5b9bf8b5533bd5c36d33f014c747ff9aa
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574337"
---
# <a name="iactivescriptstatsgetstat"></a>IActiveScriptStats::GetStat
Retourne l’une des statistiques de script standard.  
  
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
 dans Spécifie les statistiques à retourner. Doit être la valeur :  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|SCRIPTSTAT_STATEMENT_COUNT|1|Retourne le nombre d’instructions exécutées depuis le début du script ou la réinitialisation des statistiques.|  
  
 `pluHi`  
 à 32 bits de poids fort d’un entier non signé 64 bits représentant la statistique.  
  
 `pluLo`  
 à 32 bits de poids faible d’un entier non signé 64 bits représentant la statistique.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles incluent, mais ne sont pas limitées aux valeurs du tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne l’une des statistiques de script standard.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [Interface IActiveScriptStats](../../winscript/reference/iactivescriptstats-interface.md)