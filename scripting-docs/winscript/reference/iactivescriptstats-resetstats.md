---
title: IActiveScriptStats::ResetStats | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.ResetStats
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::ResetStats
ms.assetid: d98276fc-ad47-4e7b-aae4-254d63aece77
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd53cf1b91ae7eb18ccc88763437ecda44a574c9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091349"
---
# <a name="iactivescriptstatsresetstats"></a>IActiveScriptStats::ResetStats
Réinitialise les statistiques de ce script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ResetStats();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode ne prend aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode réinitialise les statistiques de ce script.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptStats](../../winscript/reference/iactivescriptstats-interface.md)