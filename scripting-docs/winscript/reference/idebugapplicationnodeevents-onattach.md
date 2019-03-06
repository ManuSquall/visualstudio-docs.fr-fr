---
title: IDebugApplicationNodeEvents::onAttach | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onAttach
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onAttach
ms.assetid: b610c7e4-1c96-47ee-958e-3a1f5f621af3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 85147e667f4e83698e23792a43020641974482a6
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091258"
---
# <a name="idebugapplicationnodeeventsonattach"></a>IDebugApplicationNodeEvents::onAttach
Gère un événement, ce qui signifie que l’objet de nœud d’application debug a été attaché à un nœud parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT onAttach(  
   IDebugApplicationNode*  prddpParent  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `prddpParent`  
 [in] Le nœud d’application de débogage qui est le parent de ce nœud.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode gère un événement, ce qui signifie que l’objet de nœud d’application debug a été attaché à un nœud parent.  
  
 Les implémenteurs de le `IDebugApplicationNode` interface déclencher cet événement.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugApplicationNodeEvents (Interface)](../../winscript/reference/idebugapplicationnodeevents-interface.md)   
 [IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)   
 [Interface IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)