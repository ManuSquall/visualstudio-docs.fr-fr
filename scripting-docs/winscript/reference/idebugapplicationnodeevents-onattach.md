---
title: "IDebugApplicationNodeEvents::onAttach | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationNodeEvents.onAttach
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugApplicationNodeEvents::onAttach"
ms.assetid: b610c7e4-1c96-47ee-958e-3a1f5f621af3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNodeEvents::onAttach
Gère un événement ce qui signifie que l'objet de nœud d'application de débogage a été attaché à un nœud parent.  
  
## Syntaxe  
  
```  
HRESULT onAttach(  
   IDebugApplicationNode*  prddpParent  
);  
```  
  
#### Paramètres  
 `prddpParent`  
 \[in\]  Le nœud d'application de débogage qui est le parent de ce nœud.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode gère un événement ce qui signifie que l'objet de nœud d'application de débogage a été attaché à un nœud parent.  
  
 Les implémenteurs de l'interface d' `IDebugApplicationNode` déclenchent cet événement.  
  
## Voir aussi  
 [IDebugApplicationNodeEvents, interface](../../winscript/reference/idebugapplicationnodeevents-interface.md)   
 [IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)   
 [IDebugApplicationNode, interface](../../winscript/reference/idebugapplicationnode-interface.md)