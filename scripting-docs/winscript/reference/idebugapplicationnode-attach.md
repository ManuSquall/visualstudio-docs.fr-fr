---
title: "IDebugApplicationNode::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationNode.Attach
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationNode::Attach"
ms.assetid: f4aad4ae-5bb0-4b5e-8f70-912a677f8f7a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNode::Attach
Ajoute ce nœud d'application à l'arborescence du projet spécifiée.  
  
## Syntaxe  
  
```  
HRESULT Attach(  
   IDebugApplicationNode*  pdanParent  
);  
```  
  
#### Paramètres  
 `pdanParent`  
 \[in\]  L'arborescence du projet où ce nœud d'application doit être ajouté.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode ajoute ce nœud d'application à l'arborescence du projet, à l'aide de `pdanParent` en tant que parent.  Si `pdanParent` est `NULL`, ce nœud d'application est le nœud de niveau supérieur.  
  
## Voir aussi  
 [IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)   
 [IDebugApplicationNode, interface](../../winscript/reference/idebugapplicationnode-interface.md)