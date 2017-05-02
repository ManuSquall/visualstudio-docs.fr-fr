---
title: "IScriptNode::GetChild | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.GetChild
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::GetChild"
ms.assetid: 8cb3f8b0-958b-40bb-a91a-49a788661861
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptNode::GetChild
Retourne l'enfant qui est à l'index spécifié dans le nœud.  
  
## Syntaxe  
  
```  
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### Paramètres  
 `isn`  
 \[in\]  L'index de l'enfant dans le parent.  
  
 `ppsn`  
 \[out\]  L'adresse d'une variable qui reçoit un pointeur vers l'interface d' `IScriptNode` de l'instance enfant.  
  
 Pour les objets d' `IScriptNode` qui représentent une page Web, retourne la valeur de ce paramètre un objet qui contient un bloc de script.  
  
 Pour les objets d' `IScriptEntry` qui spécifient un bloc de script, retourne la valeur de ce paramètre objet qui spécifie une fonction.  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Pour les objets d' `IScriptEntry` qui spécifient un objet de fonction et pour les objets d' `IScriptScriptlet` , échec de cette méthode car il n'existe aucune entrée enfant.  
  
## Voir aussi  
 [IScriptNode, interface](../../winscript/reference/iscriptnode-interface.md)