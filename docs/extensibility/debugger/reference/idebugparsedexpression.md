---
title: "IDebugParsedExpression | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugParsedExpression"
helpviewer_keywords: 
  - "Interface de IDebugParsedExpression"
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugParsedExpression
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface représente une expression analysée prête à être évaluée.  
  
## Syntaxe  
  
```  
IDebugParsedExpression : IUnknown  
```  
  
## Notes relatives à l'attention des implémenteurs  
 Un évaluateur d’expression implémente cette interface pour représenter une expression analysée est prête pour l’évaluation.  
  
## Remarques pour les appelants  
 Un appel à [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) renvoie cette interface.  
  
## Méthodes dans l'ordre Vtable  
 Le tableau suivant présente la méthode de `IDebugParsedExpression`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|Évalue l’expression analysée.|  
  
## Notes  
 Lorsque l’appelant est prêt évaluer l’expression, elle appelle [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) pour retourner une [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui contient le résultat de l’évaluation. Cette approche en deux parties de l’évaluation, l’analyse puis l’évaluation, permet à l’expression analysée être évaluées plusieurs fois, en ignorant le processus de longue durée de l’analyse de l’expression.  
  
## Configuration requise  
 En\-tête : ee.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)