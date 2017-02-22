---
title: "Interfaces d’&#233;valuateur d’Expression cl&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "évaluation de l’expression [Debugging SDK], le débogage"
  - "évaluation d’expression, interfaces"
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Interfaces d’&#233;valuateur d’Expression cl&#233;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Lorsque vous écrivez un évaluateur d’expression \(EE\), ainsi que le contexte d’évaluation, vous devez maîtriser les interfaces suivantes.  
  
## Descriptions de l’interface  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
     A une méthode unique, [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), qui obtient une structure de données qui représente le point d’exécution actuel. Cette structure de données est un des trois arguments qui passe par le moteur de débogage \(DE\) pour la [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) méthode pour évaluer une expression. Cette interface est généralement implémentée par le fournisseur de symboles.  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
     A la [Lier](../../extensibility/debugger/reference/idebugbinder-bind.md) méthode qui obtient la zone de mémoire qui contient la valeur actuelle d’un symbole. Étant donné les deux la méthode conteneur, représentée par un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) objet et le symbole lui\-même, représenté par un [IDebugField](../../extensibility/debugger/reference/idebugfield.md) objet, `IDebugBinder::Bind` retourne la valeur du symbole.`IDebugBinder` est généralement implémentée par le DE.  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
     Représente un type de données simple. Pour des types complexes, tels que des tableaux et des méthodes, utiliser dérivé [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) et [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) interfaces, respectivement.[IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) est une autre interface dérivée importante qui représente des symboles contenant les autres symboles, tels que les méthodes ou classes. Le `IDebugField` interface \(et ses dérivés\) sont généralement implémentées par le fournisseur de symboles.  
  
     Un `IDebugField` objet peut être utilisé pour rechercher le nom et le type d’un symbole et avec une [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) d’objets, peut être utilisé pour rechercher sa valeur.  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
     Représente les bits réels de la valeur d’exécution d’un symbole.[Lier](../../extensibility/debugger/reference/idebugbinder-bind.md) prend un [IDebugField](../../extensibility/debugger/reference/idebugfield.md) objet, qui représente un symbole et retourne un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) objet. Le [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) méthode retourne la valeur du symbole dans une mémoire tampon. En général, un D’implémente cette interface pour représenter la valeur d’une propriété dans la mémoire.  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
     Cette interface représente l’évaluateur d’expression lui\-même. La méthode clé est [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), qui retourne un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) interface.  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
     Cette interface représente une expression analysée prête à être évaluée. La méthode clé est [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) qui retourne un IDebugProperty2 qui représente la valeur et le type de l’expression.  
  
-   [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)  
  
     Cette interface représente une valeur et son type et le résultat de l’évaluation d’une expression.  
  
## Voir aussi  
 [Contexte d’évaluation](../../extensibility/debugger/evaluation-context.md)