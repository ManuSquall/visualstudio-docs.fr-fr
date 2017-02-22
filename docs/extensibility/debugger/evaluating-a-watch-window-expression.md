---
title: "&#201;valuation d&#39;une Expression de la fen&#234;tre Espion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Expressions de fenêtre Espion"
  - "Fenêtre Espion, expressions"
  - "évaluation d'expression, expressions de fenêtre Espion"
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# &#201;valuation d&#39;une Expression de la fen&#234;tre Espion
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d'implémenter des évaluateurs d'expression est déconseillée. Pour plus d'informations sur l'implémentation des évaluateurs d'expression CLR, consultez [évaluateurs d'Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d'évaluateur d'Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Lors de l'exécution est suspendue, Visual Studio appelle le moteur de débogage \(DE\) pour déterminer la valeur actuelle de chaque expression dans sa liste de surveillance. Le D'évalue chaque expression à l'aide d'un évaluateur d'expression \(EE\) et Visual Studio affiche sa valeur dans le **Espion** fenêtre.  
  
 Voici une vue d'ensemble du mode d'évaluation est une expression Espion de la liste :  
  
1.  Visual Studio appelle de la DE [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) pour obtenir le contexte d'une expression qui peut être utilisé pour évaluer des expressions.  
  
2.  Pour chaque expression dans la liste d'observation, Visual Studio appelle [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) pour convertir le texte de l'expression dans une expression analysée.  
  
3.  `IDebugExpressionContext2::ParseText` appels [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) pour effectuer le travail réel de l'analyse du texte et générer un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) objet.  
  
4.  `IDebugExpressionContext2::ParseText` Crée un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objet et y place le `IDebugParsedExpression` objet. Ce que je`DebugExpression2` objet est ensuite renvoyé à Visual Studio.  
  
5.  Appels de Visual Studio [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) pour évaluer l'expression analysée.  
  
6.  `IDebugExpression2::EvaluateSync` passe l'appel à [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) pour effectuer l'évaluation et de produire un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objet renvoyé à Visual Studio.  
  
7.  Appels de Visual Studio [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) pour obtenir la valeur de l'expression qui est ensuite affichée dans la liste de suivi.  
  
## Analyser, puis évaluer  
 Étant donné que l'analyse d'une expression complexe peut prendre beaucoup plu de l'évaluation, le processus d'évaluation d'une expression est divisé en deux étapes: 1\) d'analyser l'expression et \(2\) d'évaluer l'expression analysée. De cette façon, l'évaluation peut se produire plusieurs fois, mais l'expression doit être analysé qu'une seule fois. L'expression analysée intermédiaire est retournée à partir de la EE dans un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) objet encapsulé et retourné à partir de la DE comme à son tour une [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objet. Le `IDebugExpression` objet diffère l'évaluation tous à la `IDebugParsedExpression` objet.  
  
> [!NOTE]
>  Il n'est pas nécessaire pour une EE adhérer à ce processus en deux étapes, bien que Visual Studio suppose le EE peut analyser et évaluer dans la même étape lorsque [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) est appelé \(Voici comment fonctionne l'exemple MyCEE, par exemple\). Si votre langage peut former des expressions complexes, vous souhaiterez peut\-être séparer l'étape d'analyse de l'étape d'évaluation. Cela peut augmenter les performances dans le débogueur Visual Studio lorsque plusieurs expressions espionnes sont affichés.  
  
## Dans cette section  
 [Exemple d'implémentation de l'évaluation d'Expression](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 Utilise l'exemple MyCEE pour parcourir le processus d'évaluation de l'expression.  
  
 [L'évaluation d'une Expression espionne](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 Explique ce qui se produit après une analyse de l'expression réussie.  
  
## Rubriques connexes  
 [Contexte d’évaluation](../../extensibility/debugger/evaluation-context.md)  
 Fournit les arguments qui sont passés lorsque le moteur de débogage \(DE\) appelle l'évaluateur d'expression \(EE\).  
  
## Voir aussi  
 [Écriture d'un évaluateur d'Expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)