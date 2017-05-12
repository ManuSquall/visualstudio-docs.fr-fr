---
title: "IDebugApplicationNodeEvents::onDetach | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationNodeEvents.onDetach
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugApplicationNodeEvents::onDetach"
ms.assetid: ef0cbe40-8c52-4bc9-bed0-9fc508abec6e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNodeEvents::onDetach
Gère un événement ce qui signifie que l'objet de nœud d'application de débogage a été détaché d'un nœud parent.  
  
## Syntaxe  
  
```  
HRESULT onDetach();  
```  
  
#### Paramètres  
 Cette méthode n'accepte pas de paramètres.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode gère un événement ce qui signifie que l'objet de nœud d'application de débogage a été détaché d'un nœud parent.  
  
 Les implémenteurs de l'interface d' `IDebugApplicationNode` déclenchent cet événement.  
  
## Voir aussi  
 [IDebugApplicationNodeEvents, interface](../../winscript/reference/idebugapplicationnodeevents-interface.md)   
 [IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)   
 [IDebugApplicationNode, interface](../../winscript/reference/idebugapplicationnode-interface.md)