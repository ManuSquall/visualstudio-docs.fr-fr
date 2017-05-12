---
title: "IDebugApplication::CreateApplicationNode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.CreateApplicationNode
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::CreateApplicationNode"
ms.assetid: 1a1414f6-df14-4c56-b39a-8384cf16174a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::CreateApplicationNode
Crée un nœud d'application qui est associé à un fournisseur de document spécifique.  
  
## Syntaxe  
  
```  
HRESULT CreateApplicationNode(  
   IDebugApplicationNode**  ppdanNew  
);  
```  
  
#### Paramètres  
 `ppdanNew`  
 \[out\]  Le nœud d'application associé à ce fournisseur de document.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Le nouveau nœud d'application n'est pas visible tant qu'il est attaché à un nœud parent.  
  
## Voir aussi  
 [IDebugApplication, interface](../../winscript/reference/idebugapplication-interface.md)