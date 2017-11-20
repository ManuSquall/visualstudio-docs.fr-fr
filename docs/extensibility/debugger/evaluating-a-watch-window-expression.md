---
title: "L’évaluation d’une Expression de la fenêtre Espion | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 03a74bf73f457009a6f17f8e7bdda8e4e7b9e35f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="evaluating-a-watch-window-expression"></a>L’évaluation d’une Expression de la fenêtre Espion
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Lorsque l’exécution s’arrête, Visual Studio appelle le moteur de débogage (DE) pour déterminer la valeur actuelle de chaque expression contenue dans sa liste de surveillance. Le D’évalue chaque expression à l’aide d’un évaluateur d’expression (EE) et Visual Studio affiche sa valeur dans le **espion** fenêtre.  
  
 Voici une vue d’ensemble du mode d’évaluation d’expression espionne liste :  
  
1.  Visual Studio appelle de la DE [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) pour obtenir le contexte d’une expression qui peut être utilisé pour évaluer des expressions.  
  
2.  Pour chaque expression dans la liste d’observation, Visual Studio appelle [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) pour convertir le texte de l’expression dans une expression analysée.  
  
3.  `IDebugExpressionContext2::ParseText`appels [analyser](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) pour effectuer le travail réel de l’analyse du texte et générer un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) objet.  
  
4.  `IDebugExpressionContext2::ParseText`Crée un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objet et met le `IDebugParsedExpression` objet. Ce que je`DebugExpression2` est ensuite retourné à Visual Studio.  
  
5.  Appels de Visual Studio [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) pour évaluer l’expression analysée.  
  
6.  `IDebugExpression2::EvaluateSync`passe l’appel à [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) pour effectuer l’évaluation et de produire un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objet qui est retourné à Visual Studio.  
  
7.  Appels de Visual Studio [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) pour obtenir la valeur de l’expression est alors affichée dans la liste de suivi.  
  
## <a name="parse-then-evaluate"></a>Analyser, puis évaluer  
 Étant donné que l’analyse d’une expression complexe peut prendre beaucoup plus longue que l’évaluer, le processus de l’évaluation d’une expression est divisé en deux étapes : 1) analyse de l’expression et (2) d’évaluer l’expression analysée. De cette manière, l’évaluation peut se produire plusieurs fois, mais l’expression doit être analysée une seule fois. L’expression analysée intermédiaire est retournée à partir de la EE dans un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) objet encapsulé et retourné à partir de la DE comme à son tour une [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objet. Le `IDebugExpression` diffère de l’objet tous d’évaluation à la `IDebugParsedExpression` objet.  
  
> [!NOTE]
>  Il n’est pas nécessaire pour une EE adhérer à ce processus en deux étapes, bien que Visual Studio suppose que cela ; le EE peut analyser et évaluer dans la même étape lorsque [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) est appelé (c’est l’exemple MyCEE fonctionne, par exemple). Si votre langage peut former des expressions complexes, vous voudrez séparer l’étape d’analyse de l’étape d’évaluation. Cela peut augmenter les performances dans le débogueur Visual Studio lorsque plusieurs expressions espionnes sont affichés.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Exemple d’implémentation de l’évaluation d’expression](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 Utilise l’exemple MyCEE pour parcourir le processus d’évaluation de l’expression.  
  
 [Évaluation d’une expression espionne](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 Explique que se passe-t-il après une analyse de l’expression réussie.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Contexte d’évaluation](../../extensibility/debugger/evaluation-context.md)  
 Fournit les arguments sont transmis lorsque le moteur de débogage (DE) appelle l’évaluateur d’expression (EE).  
  
## <a name="see-also"></a>Voir aussi  
 [L’écriture d’un évaluateur d’Expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)