---
title: "IScriptNode::GetParent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.GetParent
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::GetParent"
ms.assetid: 0fb813f6-ab94-46b2-b0cf-ef5d1cd38ae4
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IScriptNode::GetParent
Retourne l'objet d' `IScriptNode` qui est le parent d'un objet.  
  
## Syntaxe  
  
```  
HRESULT GetParent(  
   IScriptNode       **ppsnParent  
);  
```  
  
#### Paramètres  
 `ppsnParent`  
 \[out\]  L'adresse d'une variable qui reçoit un pointeur vers l'interface d' `IScriptNode` de l'instance parente.  
  
 Si la classe implémente `IScriptEntry` ou `IScriptScriptlet`, un objet d' `IScriptNode` est retourné.  
  
 Si la classe implémente `IScriptNode`\(représentant une page Web\), NULL est retournée.  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
  
## Voir aussi  
 [IScriptNode, interface](../../winscript/reference/iscriptnode-interface.md)