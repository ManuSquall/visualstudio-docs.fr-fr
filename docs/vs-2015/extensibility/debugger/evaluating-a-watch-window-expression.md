---
title: Évaluation d’une Expression de la fenêtre Espion | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7771d8e2d8a75e5c197d3fe41f980a46581fce97
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501665"
---
# <a name="evaluating-a-watch-window-expression"></a>Évaluation d’une expression de fenêtre Espion
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [évaluation d’une Expression de la fenêtre Espion](https://docs.microsoft.com/visualstudio/extensibility/debugger/evaluating-a-watch-window-expression).  
  
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Lors de l’exécution s’interrompt, Visual Studio appelle le moteur de débogage (dé) pour déterminer la valeur actuelle de chaque expression dans sa liste de suivi. Le D’évalue chaque expression à l’aide d’un évaluateur d’expression (EE) et Visual Studio affiche sa valeur dans le **espion** fenêtre.  
  
 Voici une vue d’ensemble de la façon dont une expression de liste de suivi est évaluée :  
  
1.  Visual Studio appelle l’Allemagne [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) pour obtenir le contexte d’une expression qui peut être utilisé pour évaluer des expressions.  
  
2.  Pour chaque expression dans la liste de suivi, Visual Studio appelle [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) pour convertir le texte de l’expression en une expression analysée.  
  
3.  `IDebugExpressionContext2::ParseText` appels [analyser](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) pour effectuer le travail réel de l’analyse de texte et produire un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) objet.  
  
4.  `IDebugExpressionContext2::ParseText` Crée un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objet et y place le `IDebugParsedExpression` objet dedans. Ce que je`DebugExpression2` objet est ensuite renvoyé à Visual Studio.  
  
5.  Les appels de Visual Studio [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) pour évaluer l’expression analysée.  
  
6.  `IDebugExpression2::EvaluateSync` passe l’appel à [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) pour effectuer l’évaluation et de produire un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objet qui est retourné à Visual Studio.  
  
7.  Les appels de Visual Studio [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) pour obtenir la valeur de l’expression est alors affichée dans la liste de suivi.  
  
## <a name="parse-then-evaluate"></a>Analyser, puis évaluer  
 Étant donné que l’analyse d’une expression complexe peut prendre beaucoup plus longue que l’évaluer, le processus d’évaluation d’une expression est divisé en deux étapes : 1) analyse de l’expression et (2) d’évaluer l’expression analysée. De cette façon, l’évaluation peut se produire plusieurs fois, mais l’expression doit être analysé qu’une seule fois. L’expression analysée intermédiaire est retournée à partir de la EE dans un [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) objet encapsulé à son tour et retournée à partir de l’Allemagne comme un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objet. Le `IDebugExpression` objet diffère de l’évaluation toutes les le `IDebugParsedExpression` objet.  
  
> [!NOTE]
>  Il n’est pas nécessaire pour un EE à adhérer à ce processus en deux étapes, même si Visual Studio considère cela ; le EE peut analyser et évaluer dans la même étape lorsque [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) est appelée (c’est l’exemple MyCEE fonctionne, par exemple). Si votre langage peut former des expressions complexes, vous souhaiterez séparer l’étape d’analyse de l’étape d’évaluation. Cela peut augmenter les performances dans le débogueur Visual Studio lorsque plusieurs expressions espionnes sont affichées.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Exemple d’implémentation de l’évaluation d’expression](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 Utilise l’exemple MyCEE pour parcourir le processus d’évaluation de l’expression.  
  
 [Évaluation d’une expression espionne](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 Explique ce qui se passe après une analyse de l’expression réussie.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Contexte d’évaluation](../../extensibility/debugger/evaluation-context.md)  
 Fournit les arguments sont transmis lorsque le moteur de débogage (dé) appelle l’évaluateur d’expression (EE).  
  
## <a name="see-also"></a>Voir aussi  
 [Écriture d’un évaluateur d’expression de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

