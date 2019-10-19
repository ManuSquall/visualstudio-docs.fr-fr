---
title: 'IRemoteDebugApplication :: CauseBreak | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.CauseBreak
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::CauseBreak
ms.assetid: 6a2c27bb-dca0-475c-9918-bdbb70a50d26
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8107d7f8450df759b53175505c8d7fc2b6bde641
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571512"
---
# <a name="iremotedebugapplicationcausebreak"></a>IRemoteDebugApplication::CauseBreak
Entraîne l’arrêt de l’application dans le débogueur au plus tôt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CauseBreak();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode n’accepte aucun paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 L’appel de cette méthode n’entraîne pas l’arrêt immédiat d’une application. Si l’application n’exécute pas de code de script, un certain temps peut s’écouler avant que l’application ne s’arrête réellement.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)