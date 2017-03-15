---
title: "IDebugParsedExpression::EvaluateSync | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugParsedExpression::EvaluateSync"
helpviewer_keywords: 
  - "IDebugParsedExpression::EvaluateSync (méthode)"
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugParsedExpression::EvaluateSync
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode évalue l'expression analysée et effectue un cast éventuellement le résultat en un autre type de données.  
  
## Syntaxe  
  
```cpp#  
HRESULT EvaluateSync(   
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BSTR                  bstrResultType,  
   IDebugProperty2**     ppResult  
);  
```  
  
```c#  
int EvaluateSync(  
   uint                 dwEvalFlags,   
   uint                 dwTimeout,   
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   string               bstrResultType,   
   out IDebugProperty2  ppResult  
);  
```  
  
#### Paramètres  
 `dwEvalFlags`  
 \[in\]  Une combinaison des constantes d' [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) qui contrôlent l'expression sera évaluée.  
  
 `dwTimeout`  
 \[in\]  Spécifie le temps maximum, en millisecondes, d'attendre avant le retour de cette méthode.  Utilisation `INFINITE` d'attente dure indéfiniment.  
  
 `pSymbolProvider`  
 \[in\]  Le fournisseur de symbole, exprimé sous la forme d'une interface d' [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) .  
  
 `pAddress`  
 \[in\]  L'emplacement en cours de exécution dans une méthode, exprimée comme une interface d' [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
 `pBinder`  
 \[in\]  Le classeur, exprimé sous la forme d'une interface d' [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) .  
  
 `bstrResultType`  
 \[in\]  Le type le résultat doit être casté en.  cet argument peut être une valeur NULL.  
  
 `ppResult`  
 \[out\]  Retourne l'interface d' [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui représente les résultats de l'évaluation.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Le contexte d'évaluation de l'expression est fourni par`pAddress`, qui permet de déterminer la méthode conteneur puis utiliser les règles de portée de langage de déterminer la valeur des symboles dans l'expression.  
  
## Voir aussi  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)