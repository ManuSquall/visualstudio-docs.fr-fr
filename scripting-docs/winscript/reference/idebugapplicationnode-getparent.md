---
title: "IDebugApplicationNode::GetParent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationNode.GetParent
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationNode::GetParent"
ms.assetid: 88ba3a53-0cd7-4e1f-8558-79c20ac76cc9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNode::GetParent
Retourne le nœud parent de ce nœud d'application.  
  
## Syntaxe  
  
```  
HRESULT GetParent(  
   IDebugApplicationNode**  pprddp  
);  
```  
  
#### Paramètres  
 `pprddp`  
 \[out\]  Nœud d'application parent de ce nœud d'application.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode retourne le nœud parent de ce nœud d'application.  
  
## Voir aussi  
 [IDebugApplicationNode, interface](../../winscript/reference/idebugapplicationnode-interface.md)