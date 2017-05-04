---
title: "IDebugExpression::GetResultAsString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpression.GetResultAsString
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpression::GetResultAsString"
ms.assetid: edadd2ad-9369-4878-bf87-cea15be9f363
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression::GetResultAsString
Retourne le résultat de l'évaluation d'une expression sous forme de chaîne et valeur de retour de l'exécution.  
  
## Syntaxe  
  
```  
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### Paramètres  
 `phrResult`  
 \[out\]  la valeur de retour de l'exécution.  
  
 `pbstrResult`  
 \[out\]  le résultat de l'évaluation de l'expression.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_PENDING`|L'exécution est en attente.|  
  
## Notes  
 Cette méthode retourne le résultat de l'évaluation d'une expression sous forme de chaîne et `HRESULT`de l'exécution.  
  
 Cette méthode retourne `S_OK` et `phrResult` retourne `E_ABORT` si `Abort` interrompt l'exécution.  
  
## Voir aussi  
 [IDebugExpression, interface](../../winscript/reference/idebugexpression-interface.md)