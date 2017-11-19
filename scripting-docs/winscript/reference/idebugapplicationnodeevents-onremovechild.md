---
title: IDebugApplicationNodeEvents::onRemoveChild | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplicationNodeEvents.onRemoveChild
apilocation: scrobj.dll
helpviewer_keywords: IDebugApplicationNodeEvents::onRemoveChild
ms.assetid: 2e025d29-b8c0-4793-a2d3-c20d548d6386
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a62f187286f66f8adff8acda339e02a02bc6225
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnodeeventsonremovechild"></a>IDebugApplicationNodeEvents::onRemoveChild
Gère l’événement lorsqu’un nœud enfant est supprimé d’un objet de nœud d’application de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT onRemoveChild(  
   IDebugApplicationNode*  prddpChild  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `prddpChild`  
 [in] Le nœud d’application enfants qui a été supprimé.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode gère l’événement lorsqu’un nœud enfant est supprimé d’un objet de nœud d’application de débogage.  
  
 Les implémenteurs de le `IDebugApplicationNode` interface déclencher cet événement.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugApplicationNodeEvents (Interface)](../../winscript/reference/idebugapplicationnodeevents-interface.md)   
 [IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)   
 [Interface IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)