---
title: "IDebugDocumentHelper::GetDebugApplicationNode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.GetDebugApplicationNode
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::GetDebugApplicationNode"
ms.assetid: ecd18803-beb4-4ac2-9702-cc9e8a12c395
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::GetDebugApplicationNode
Retourne le nœud d'application de débogage correspondant à ce document.  
  
## Syntaxe  
  
```  
HRESULT GetDebugApplicationNode(  
   IDebugApplicationNode**  ppdan  
);  
```  
  
#### Paramètres  
 `ppdan`  
 \[out\]  Le nœud d'application de débogage correspondant à ce document.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Retourne le nœud d'application de débogage correspondant à ce document.  
  
## Voir aussi  
 [IDebugDocumentHelper, interface](../../winscript/reference/idebugdocumenthelper-interface.md)