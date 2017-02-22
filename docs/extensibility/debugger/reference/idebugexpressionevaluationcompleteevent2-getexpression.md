---
title: "IDebugExpressionEvaluationCompleteEvent2::GetExpression | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluationCompleteEvent2::GetExpression"
helpviewer_keywords: 
  - "IDebugExpressionEvaluationCompleteEvent2::GetExpression"
ms.assetid: faf6b2dd-2afd-4852-b21c-7e8d3130e141
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugExpressionEvaluationCompleteEvent2::GetExpression
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient l'expression d'origine.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetExpression(   
   IDebugExpression2** ppExpr  
);  
```  
  
```c#  
int GetExpression(   
   out IDebugExpression2 ppExpr  
);  
```  
  
#### Paramètres  
 `ppExpr`  
 \[out\]  Retourne un objet d' [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) qui représente l'expression qui a été analysée.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode retourne l'objet qui a été créé dans un appel à la méthode d' [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) .  
  
## Voir aussi  
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)