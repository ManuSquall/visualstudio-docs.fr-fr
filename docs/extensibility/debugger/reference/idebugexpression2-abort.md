---
title: "IDebugExpression2::Abort | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpression2::Abort"
helpviewer_keywords: 
  - "IDebugExpression2::Abort"
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpression2::Abort
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode annule l'évaluation d'une expression asynchrone comme démarré par un appel à la méthode d' [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) .  
  
## Syntaxe  
  
```cpp#  
HRESULT Abort(  
   void  
);  
```  
  
```c#  
int Abort();  
```  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Lorsque l'évaluation de l'expression asynchrone est annulée, faites pas envoyé un événement d' [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) au rappel d'événement passé aux méthodes d' [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) ou d' [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .  
  
## Voir aussi  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)