---
title: IRemoteDebugApplicationEvents::OnDebugOutput | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 022a2297e135f308a8250fa0b493dd5943da7687
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728639"
---
# <a name="iremotedebugapplicationeventsondebugoutput"></a>IRemoteDebugApplicationEvents::OnDebugOutput
Gère un événement de sortie du débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OnDebugOutput(  
   LPCOLESTR  pstr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstr`  
 [in] La chaîne de sortie de débogage.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode gère l’événement de sortie du débogueur.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md)