---
title: "IDebugExpression::GetResultAsDebugProperty | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpression.GetResultAsDebugProperty
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpression::GetResultAsDebugProperty"
ms.assetid: 9075bf2f-d5bb-464e-b6c2-3fa3215e9ae0
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression::GetResultAsDebugProperty
Retourne le résultat de l'évaluation de l'expression comme propriété de débogage et valeur de retour de l'exécution.  
  
## Syntaxe  
  
```  
HRESULT GetResultAsDebugProperty(  
   HRESULT*          phrResult,  
   IDebugProperty**  ppdp  
);  
```  
  
#### Paramètres  
 `phrResult`  
 \[out\]  la valeur de retour de l'exécution.  
  
 `ppdp`  
 \[out\]  la propriété de débogage pour l'expression.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_PENDING`|L'exécution est en attente.|  
  
## Notes  
 Cette méthode retourne le résultat de l'évaluation de l'expression comme `IDebugProperty` et `HRESULT`de l'exécution.  
  
 Cette méthode retourne `S_OK` et `phrResult` retourne `E_ABORT` si `Abort` interrompt l'exécution.  
  
## Voir aussi  
 [IDebugExpression, interface](../../winscript/reference/idebugexpression-interface.md)   
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)