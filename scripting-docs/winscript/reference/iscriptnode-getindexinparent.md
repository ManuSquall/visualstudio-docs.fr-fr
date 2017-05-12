---
title: "IScriptNode::GetIndexInParent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.GetIndexInParent
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::GetIndexInParent"
ms.assetid: 521c1ca1-2d27-4344-bf3b-d8b53132b648
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IScriptNode::GetIndexInParent
Retourne l'index d'un objet de la liste enfant du parent.  
  
## Syntaxe  
  
```  
HRESULT GetIndexInParent(  
   ULONG              pisn,  
);  
```  
  
#### Paramètres  
 `pisn`  
 \[out\]  Retourne l'index d'un objet de la liste enfant du parent.  
  
 Si cette méthode est appelée par un objet d' `IScriptNode` qui représente une page Web, retourne 0 de ce paramètre.  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
  
## Voir aussi  
 [IScriptNode, interface](../../winscript/reference/iscriptnode-interface.md)