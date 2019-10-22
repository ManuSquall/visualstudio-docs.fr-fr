---
title: 'IDebugSyncOperation :: GetTargetThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.GetTargetThread
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::GetTargetThread
ms.assetid: e6eeeb90-b5ed-4727-8434-fa3186c25013
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6675356439d60e5c204760e69640a0f50bf40fc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576686"
---
# <a name="idebugsyncoperationgettargetthread"></a>IDebugSyncOperation::GetTargetThread
Retourne le thread d’application cible pour cette opération synchrone.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetTargetThread(  
   IDebugApplicationThread**  ppatTarget  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppatTarget`  
 à Thread d’application cible pour cette opération synchrone.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne le thread d’application cible pour cette opération synchrone.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)