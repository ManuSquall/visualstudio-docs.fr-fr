---
title: "IEnumDebugApplicationNodes::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugApplicationNodes.Clone
apilocation: pdm.dll
helpviewer_keywords: 
  - "IEnumDebugApplicationNodes::Clone"
ms.assetid: 7190954d-e2da-4a84-8e37-81d4d27886a8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugApplicationNodes::Clone
Crée un énumérateur qui contient le même état que l'énumérateur en cours.  
  
## Syntaxe  
  
```  
HRESULT Clone(  
   IEnumDebugApplicationNodes**  pperddp  
);  
```  
  
#### Paramètres  
 `pperddp`  
 \[out\]  Retourne l'interface d' `IEnumDebugApplicationNodes` de clone de l'énumérateur.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode crée un énumérateur qui contient le même état que l'énumérateur actuel.  
  
## Voir aussi  
 [IEnumDebugApplicationNodes, interface](../../winscript/reference/ienumdebugapplicationnodes-interface.md)