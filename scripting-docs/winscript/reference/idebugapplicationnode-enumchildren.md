---
title: "IDebugApplicationNode::EnumChildren | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationNode.EnumChildren
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationNode::EnumChildren"
ms.assetid: d79b362b-23d5-4a5e-a214-5a78618eaf71
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNode::EnumChildren
Énumère les nœuds enfants de ce nœud d'application.  
  
## Syntaxe  
  
```  
HRESULT EnumChildren(  
   IEnumDebugApplicationNodes**  pperddp  
);  
```  
  
#### Paramètres  
 `pperddp`  
 \[out\]  L'énumération des nœuds enfants de ce nœud.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode énumère les nœuds enfants de ce nœud d'application.  
  
## Voir aussi  
 [IDebugApplicationNode, interface](../../winscript/reference/idebugapplicationnode-interface.md)