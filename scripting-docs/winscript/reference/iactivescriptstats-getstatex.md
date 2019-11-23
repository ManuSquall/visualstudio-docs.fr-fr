---
title: IActiveScriptStats::GetStatEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStatEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStatEx
ms.assetid: f526f51d-8ab5-49ef-a8f7-ae0ac1cb46e4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ca7cdb81fd7e228b26bfaa12d45e81335674a74
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576124"
---
# <a name="iactivescriptstatsgetstatex"></a>IActiveScriptStats::GetStatEx
Retourne une statistique de script personnalisé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `guid`  
 dans Spécifie les statistiques à retourner. La sémantique de laquelle les statistiques correspondent à un GUID particulier est entièrement définie par le moteur.  
  
 `pluHi`  
 à 32 bits de poids fort d’un entier non signé 64 bits représentant la statistique.  
  
 `pluLo`  
 à 32 bits de poids faible d’un entier non signé 64 bits représentant la statistique.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_NOTIMPL`|Cette méthode n'est pas implémentée.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode permet à un moteur de script personnalisé de retourner des statistiques explicites à un hôte personnalisé.  
  
> [!NOTE]
> Cette méthode n'est pas implémentée à l'heure actuelle.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)   
 [Interface IActiveScriptStats](../../winscript/reference/iactivescriptstats-interface.md)