---
title: IDebugApplicationNodeEvents::onAddChild | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplicationNodeEvents.onAddChild
apilocation: scrobj.dll
helpviewer_keywords: IDebugApplicationNodeEvents::onAddChild
ms.assetid: 59ce33cf-1843-4b03-98a2-34859d3023f7
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3df872cd14b6d7fcd455371d1601b2a4082fb39a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnodeeventsonaddchild"></a>IDebugApplicationNodeEvents::onAddChild
Gère l’événement lorsqu’un nœud enfant est ajouté à un objet de nœud d’application de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT onAddChild(  
   IDebugApplicationNode*  prddpChild  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `prddpChild`  
 [in] Le nœud application de débogage enfant qui a été ajouté.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode gère l’événement lorsqu’un nœud enfant est ajouté à un objet de nœud d’application de débogage.  
  
 Les implémenteurs de le `IDebugApplicationNode` interface déclencher cet événement  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugApplicationNodeEvents (Interface)](../../winscript/reference/idebugapplicationnodeevents-interface.md)   
 [IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)   
 [Interface IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)