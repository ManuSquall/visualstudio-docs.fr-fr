---
title: "&#201;valuation de l&#39;expression en Mode arr&#234;t | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "en mode arrêt, évaluation d'expression"
  - "évaluation de l'expression [Debugging SDK], le débogage"
  - "évaluation de l'expression en mode arrêt"
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# &#201;valuation de l&#39;expression en Mode arr&#234;t
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les éléments suivants décrivent le processus qui se produit lorsque le débogueur est en mode arrêt et doit effectuer l'évaluation de l'expression.  
  
## Processus d'évaluation de l'expression  
 Ce sont les étapes de base à exécuter lors de l'évaluation d'une expression :  
  
1.  le gestionnaire de débogage de session \(SDM\) appelle [IDebugStackFrame2 : : GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) pour obtenir une interface de contexte d'expression, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2.  Le SDM appelle ensuite [IDebugExpressionContext2 : : ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) avec la chaîne à analyser.  
  
3.  Si ParseText ne retourne pas S\_OK, la raison de l'erreur est retournée.  
  
     \- sinon  
  
     Si ParseText retourne S\_OK, le SDM peut ensuite appeler [IDebugExpression2 : : EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [IDebugExpression2 : : EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) pour obtenir une valeur finale de l'expression analysée.  
  
    -   Dans le cas de utilisation `IDebugExpression2::EvaluateSync`, l'interface de rappel données sont utilisées pour communiquer le processus actuel de l'évaluation.  la valeur finale est retournée dans une interface d' [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) .  
  
    -   Dans le cas de utilisation `IDebugExpression2::EvaluateAsync`, l'interface de rappel données sont utilisées pour communiquer le processus actuel de l'évaluation.  Une fois que l'évaluation est terminée, EvaluateAsync envoie une interface d' [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) via le rappel.  Avec cette interface d'événement, la dernière valeur peut être obtenue avec [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).  
  
## Voir aussi  
 [Appeler les événements de débogueur](../../extensibility/debugger/calling-debugger-events.md)