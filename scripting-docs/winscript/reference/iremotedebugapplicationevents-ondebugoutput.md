---
title: 'IRemoteDebugApplicationEvents :: OnDebugOutput | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEvents.OnDebugOutput
apilocation:
- jscript.dll
helpviewer_keywords:
- IRemoteDebugApplicationEvents::OnDebugOutput
ms.assetid: db08872e-3d84-4d7f-bf94-a851bf43a333
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 34b03f65dd25afdab5f438bcddb6dd0b7711644f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572740"
---
# <a name="iremotedebugapplicationeventsondebugoutput"></a>IRemoteDebugApplicationEvents::OnDebugOutput
Gère un événement de sortie du débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OnDebugOutput(  
   LPCOLESTR  pstr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstr`  
 dans Chaîne de sortie de débogage.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode gère l’événement de sortie du débogueur.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md)