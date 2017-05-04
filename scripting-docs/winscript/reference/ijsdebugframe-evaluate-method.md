---
title: "IJsDebugFrame::Evaluate, m&#233;thode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.Evaluate
apilocation: jscript9diag.dll
ms.assetid: 0ee61340-37b8-4fbb-a028-748b5315e279
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugFrame::Evaluate, m&#233;thode
Évaluez une expression dans le contexte de ce frame de pile.  
  
## Syntaxe  
  
```  
HRESULT Evaluate(  
   LPCOLESTR pExpressionText,  
   IJsDebugProperty **ppDebugProperty,  
   BSTR *pError  
);  
```  
  
#### Paramètres  
 `pExpressionText`  
 \[in\] Expression à évaluer.  
  
 `ppDebugProperty`  
 \[out\] Objet représentant le navigateur de propriétés.  
  
 `pError`  
 \[out\] Message d'erreur, si une erreur se produit.  
  
## Valeur de retour  
  
## Notes  
 Retourne ce qui suit : S\_OK : l'évaluation a réussi, \*ppDebugProperty contient le résultat de l'évaluation.  S\_FALSE : l'évaluation génère une erreur \(ou l'opération d'évaluation n'est pas prise en charge\), \*pError contient le message d'erreur.  
  
## Configuration requise  
 **En\-tête :** jscript9diag.h  
  
## Voir aussi  
 [IJsDebugFrame, interface](../../winscript/reference/ijsdebugframe-interface.md)