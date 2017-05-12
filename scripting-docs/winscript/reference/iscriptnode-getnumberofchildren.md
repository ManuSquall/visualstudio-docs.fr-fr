---
title: "IScriptNode::GetNumberOfChildren | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.GetNumberOfChildren
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::GetNumberOfChildren"
ms.assetid: 3451c7e9-cb50-482e-9038-6e7d7ce1ecdf
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IScriptNode::GetNumberOfChildren
Retourne le nombre de nœuds enfants de l'objet d' `IScriptNode` .  
  
## Syntaxe  
  
```  
HRESULT GetNumberOfChildren(  
   ULONG              *pcsn  
);  
```  
  
#### Paramètres  
 `pcsn`  
 \[out\]  Le nombre de nœuds enfants que l'objet d' `IScriptNode` un.  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
  
## Voir aussi  
 [IScriptNode, interface](../../winscript/reference/iscriptnode-interface.md)