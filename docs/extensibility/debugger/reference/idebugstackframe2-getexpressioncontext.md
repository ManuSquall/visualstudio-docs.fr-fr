---
title: "IDebugStackFrame2::GetExpressionContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2::GetExpressionContext"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetExpressionContext"
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugStackFrame2::GetExpressionContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient un contexte d'évaluation de l'évaluation d'une expression dans le contexte actuel d'un frame de pile et d'un thread.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetExpressionContext (   
   IDebugExpressionContext2** ppExprCxt  
);  
```  
  
```c#  
int GetExpressionContext (   
   out IDebugExpressionContext2 ppExprCxt  
);  
```  
  
#### Paramètres  
 `ppExprCxt`  
 \[out\]  Retourne un objet d' [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) qui représente un contexte pour l'évaluation de l'expression.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 En général, un contexte d'évaluation de l'expression peut être considéré comme place de l'évaluation d'une expression.  Appelez la méthode d' [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) pour analyser une expression puis appeler les méthodes résultant d' [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou d' [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) pour évaluer l'expression analysée.  
  
## Voir aussi  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)