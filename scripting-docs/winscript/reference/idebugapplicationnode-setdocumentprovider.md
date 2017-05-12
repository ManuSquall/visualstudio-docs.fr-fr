---
title: "IDebugApplicationNode::SetDocumentProvider | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplicationNode.SetDocumentProvider
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplicationNode::SetDocumentProvider"
ms.assetid: 7cb587ca-d84e-4b5e-9b94-e973cca55a03
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationNode::SetDocumentProvider
Définit le fournisseur de le document pour ce nœud d'application.  
  
## Syntaxe  
  
```  
HRESULT SetDocumentProvider(  
   IDebugDocumentProvider*  pddp  
);  
```  
  
#### Paramètres  
 `pddp`  
 \[in\]  Le fournisseur de le document pour ce nœud d'application.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode définit le fournisseur de le document pour ce nœud d'application.  
  
## Voir aussi  
 [IDebugApplicationNode, interface](../../winscript/reference/idebugapplicationnode-interface.md)