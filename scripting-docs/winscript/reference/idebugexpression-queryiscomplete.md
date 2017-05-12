---
title: "IDebugExpression::QueryIsComplete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpression.QueryIsComplete
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpression::QueryIsComplete"
ms.assetid: 510d62e5-a316-46fb-b23f-d3ba902b295c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression::QueryIsComplete
Détermine si l'opération est terminée.  
  
## Syntaxe  
  
```  
HRESULT QueryIsComplete();  
```  
  
#### Paramètres  
 Cette méthode n'accepte pas de paramètres.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi, et l'opération est terminée.|  
|`S_FALSE`|L'exécution est en attente.|  
  
## Notes  
 Cette méthode détermine si l'opération est terminée.  
  
## Voir aussi  
 [IDebugExpression, interface](../../winscript/reference/idebugexpression-interface.md)