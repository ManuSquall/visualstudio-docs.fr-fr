---
title: "IScriptNode::GetCookie | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.GetCookie
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::GetCookie"
ms.assetid: 007339c6-a73a-4147-b3c0-cc041e467ecd
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IScriptNode::GetCookie
Retourne une valeur définie par l'application qui est utilisée pour associer un scriptlet avec l'objet hôte.  
  
## Syntaxe  
  
```  
HRESULT GetCookie(  
   DWORD              *pdwCookie  
);  
```  
  
#### Paramètres  
 `pdwCookie`  
 \[out\]  Pour un objet d' `IScriptEntry` , retourne la valeur du cookie défini par l'application.  
  
 Pour un objet d' `IScriptNode` qui représente une page Web, retourne 0.  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
  
## Voir aussi  
 [IScriptNode, interface](../../winscript/reference/iscriptnode-interface.md)