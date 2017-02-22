---
title: "IDebugExpression2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpression2"
helpviewer_keywords: 
  - "Interface de IDebugExpression2"
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugExpression2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette interface représente une expression analysée prête pour lier et évaluer.  
  
## Syntaxe  
  
```  
IDebugExpression2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 le moteur de débogage \(DE\) implémente cette interface pour représenter une expression analysée prête à être évalué.  
  
## Remarques pour les appelants  
 Un appel à [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) retourne cette interface.  [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) retourne l'interface d' [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) .  Ces interfaces sont accessibles uniquement lorsque le programme débogué a été suspendu et un frame de pile est disponible.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugExpression2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Évalue l'expression de façon asynchrone.|  
|[Abandonner](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Termine l'évaluation d'une expression asynchrone.|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Évalue cette expression de façon synchrone.|  
  
## Notes  
 Lorsqu'un programme a désactivé, le gestionnaire de débogage de session \(SDM\) obtient un frame de pile du De avec un appel à [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md).  Le SDM appelle ensuite [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) pour obtenir l'interface d' [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) .  Cela est suivi par un appel à [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) pour créer l'interface d' `IDebugExpression2` , qui représente l'expression analysée prête à être évalué.  
  
 Le SDM appelle [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) réellement pour évaluer l'expression et produire une valeur.  
  
 Dans une implémentation d' `IDebugExpressionContext2::ParseText`, la fonction d' `CoCreateInstance` de COM de pour instancier un évaluateur d'expression et pour obtenir une interface d' [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) \(consultez l'exemple de l'interface d' `IDebugExpressionEvaluator` \).  Le De appelle ensuite [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) pour obtenir une interface d' [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) .  cette interface est utilisée dans l'implémentation d' `IDebugExpression2::EvaluateSync` et d' `IDebugExpression2::EvaluateAsync` pour exécuter l'évaluation.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)