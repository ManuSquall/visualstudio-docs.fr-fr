---
title: Évaluation d’une expression de fenêtre de montre (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9cef2f27eec095ee7b136153ecb764feba9effbb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738839"
---
# <a name="evaluate-a-watch-window-expression"></a>Évaluer l’expression d’une fenêtre de montre
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, consultez [les évaluateurs de l’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon d’évaluateur d’expression gérée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Lorsque l’exécution s’arrête, Visual Studio appelle le moteur de débogé (DE) pour déterminer la valeur actuelle de chaque expression dans sa liste de surveillance. Le DE évalue chaque expression à l’aide d’un évaluateur d’expression (EE), et Visual Studio affiche sa valeur dans la fenêtre **Watch.**

 Voici un aperçu de la façon dont l’expression d’une liste de surveillance est évaluée :

1. Visual Studio appelle [getExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) du DE pour obtenir un contexte d’expression qui peut être utilisé pour évaluer les expressions.

2. Pour chaque expression de la liste de surveillance, Visual Studio appelle [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) pour convertir le texte d’expression en une expression analysée.

3. `IDebugExpressionContext2::ParseText`appelle [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) pour faire le travail réel d’analyser le texte et de produire un objet [IDebugParsedExpression.](../../extensibility/debugger/reference/idebugparsedexpression.md)

4. `IDebugExpressionContext2::ParseText`crée un objet [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) et y met l’objet. `IDebugParsedExpression` Cet`DebugExpression2` objet I est ensuite retourné à Visual Studio.

5. Visual Studio appelle [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) pour évaluer l’expression analysée.

6. `IDebugExpression2::EvaluateSync`passe l’appel à [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) pour faire l’évaluation réelle et produire un objet [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) qui est retourné à Visual Studio.

7. Visual Studio appelle [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) pour obtenir la valeur de l’expression qui est ensuite affichée dans la liste de surveillance.

## <a name="parse-then-evaluate"></a>Parse puis évaluer
 Étant donné que l’analyse d’une expression complexe peut prendre beaucoup plus de temps que de l’évaluer, le processus d’évaluation d’une expression est divisé en deux étapes : 1) analysent l’expression et 2) évaluent l’expression analysée. De cette façon, l’évaluation peut se produire plusieurs fois, mais l’expression doit être analysée qu’une seule fois. L’expression analysée intermédiaire est retournée de l’EE dans un objet [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) qui est à son tour encapsulé et retourné de la DE comme un objet [IDebugExpression2.](../../extensibility/debugger/reference/idebugexpression2.md) L’objet `IDebugExpression` reporte toute `IDebugParsedExpression` évaluation à l’objet.

> [!NOTE]
> Il n’est pas nécessaire qu’un EE adhère à ce processus en deux étapes, même si Visual Studio l’assume; l’EE peut analyser et évaluer dans la même étape lorsque [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) est appelé (c’est ainsi que fonctionne l’échantillon MyCEE, par exemple). Si votre langue peut former des expressions complexes, vous pouvez séparer l’étape d’analyse de l’étape d’évaluation. Cela peut augmenter les performances dans le Visual Studio débbugger lorsque de nombreuses expressions de montres sont montrées.

## <a name="in-this-section"></a>Contenu de cette section
 [Exemple de mise en œuvre de l’évaluation de l’expression](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md) Utilise l’échantillon MyCEE pour passer à travers le processus d’évaluation de l’expression.

 [Évaluation de l’expression d’une montre](../../extensibility/debugger/evaluating-a-watch-expression.md) Explique ce qui se passe après un analyse d’expression réussie.

## <a name="related-sections"></a>Sections connexes
 [Contexte d’évaluation](../../extensibility/debugger/evaluation-context.md) Fournit les arguments qui sont passés lorsque le moteur de débogé (DE) appelle l’évaluateur d’expression (EE).

## <a name="see-also"></a>Voir aussi
 [Rédaction d’un évaluateur d’expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
