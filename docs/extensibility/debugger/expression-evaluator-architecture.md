---
title: Architecture d’évaluateur d’expression (en anglais) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aac782c653f230d5598a49d43eb70f548de6dc41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738696"
---
# <a name="expression-evaluator-architecture"></a>Architecture d’évaluateur d’expression
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, consultez [les évaluateurs de l’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon d’évaluateur d’expression gérée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 L’intégration d’une langue propriétaire dans le package Debug Visual Studio signifie que vous devez configurer les interfaces d’évaluateur d’expression (EE) requises et appeler le fournisseur de symboles de temps d’exécution de la langue (SP) et les interfaces de liant. Les objets SP et liant, ainsi que l’adresse d’exécution actuelle, sont le contexte dans lequel les expressions sont évaluées. L’information que ces interfaces produisent et consomment représente les concepts clés de l’architecture d’un EE.

## <a name="overview"></a>Vue d'ensemble

### <a name="parse-the-expression"></a>Parse l’expression
 Lorsque vous débogage d’un programme, les expressions sont évaluées pour un certain nombre de raisons, mais toujours lorsque le programme étant débogé a été arrêté à un point d’arrêt (soit un point d’arrêt placé par l’utilisateur ou un causé par une exception). C’est à ce moment que Visual Studio obtient un cadre de pile, représenté par [l’interface IDebugStackFrame2,](../../extensibility/debugger/reference/idebugstackframe2.md) à partir du moteur de débogé (DE). Visual Studio appelle ensuite [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) pour obtenir l’interface [IDebugExpressionContext2.](../../extensibility/debugger/reference/idebugexpressioncontext2.md) Cette interface représente un contexte dans lequel les expressions peuvent être évaluées; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) est le point d’entrée du processus d’évaluation. Jusqu’à présent, toutes les interfaces sont implémentées par le DE.

 Lorsqu’il `IDebugExpressionContext2::ParseText` est appelé, le DE instantanéise l’EE associé à la langue du fichier source où le point d’arrêt s’est produit (le DE instantanéise également le SH à ce stade). L’EE est représentée par l’interface [IDebugExpressionEvaluator.](../../extensibility/debugger/reference/idebugexpressionevaluator.md) Le DE appelle ensuite [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) pour convertir l’expression (sous forme de texte) en une expression analysée, prête pour l’évaluation. Cette expression analysée est représentée par l’interface [IDebugParsedExpression.](../../extensibility/debugger/reference/idebugparsedexpression.md) L’expression est généralement analysée et non évaluée à ce stade.

 Le DE crée un objet qui implémente [l’interface IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) met `IDebugParsedExpression` l’objet dans l’objet, `IDebugExpression2` et renvoie l’objet `IDebugExpression2` à partir de `IDebugExpressionContext2::ParseText`.

### <a name="evaluate-the-expression"></a>Évaluer l’expression
 Visual Studio appelle [Soit EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) pour évaluer l’expression analysée. Ces deux méthodes appellent [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (appelle`IDebugExpression2::EvaluateSync` `IDebugExpression2::EvaluateAsync` la méthode immédiatement, tandis que les appelle la méthode à travers un fil d’arrière-plan) pour évaluer l’expression analysée et retourner une interface [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) qui représente la valeur et le type de l’expression analysée. `IDebugParsedExpression::EvaluateSync`utilise le SH fourni, l’adresse et le liant pour convertir l’expression analysée en une valeur réelle, représentée par l’interface. `IDebugProperty2`

### <a name="for-example"></a>Par exemple
 Une fois qu’un point d’arrêt est atteint dans un programme en cours d’exécution, l’utilisateur choisit de visualiser une variable dans la boîte de dialogue **QuickWatch.** Cette boîte de dialogue montre le nom de la variable, sa valeur et son type. L’utilisateur peut généralement modifier la valeur.

 Lorsque la boîte de dialogue **QuickWatch** est affichée, le nom de la variable examinée est envoyé sous forme de texte à [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Cela renvoie un objet [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) représentant l’expression analysée, dans ce cas, la variable. [AssessSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) est alors appelé `IDebugProperty2` à produire un objet qui représente la valeur et le type de la variable, ainsi que son nom. C’est cette information qui est affichée.

 Si l’utilisateur modifie la valeur de la variable, [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) est appelé avec la nouvelle valeur, ce qui modifie la valeur de la variable dans la mémoire de sorte qu’il sera utilisé lorsque le programme reprend en cours d’exécution.

 Voir [Afficher les habitants](../../extensibility/debugger/displaying-locals.md) pour plus de détails sur ce processus d’affichage des valeurs des variables. Voir [Changer la valeur d’un local](../../extensibility/debugger/changing-the-value-of-a-local.md) pour plus de détails sur la façon dont la valeur d’une variable est modifiée.

## <a name="in-this-section"></a>Contenu de cette section
 [Contexte d’évaluation](../../extensibility/debugger/evaluation-context.md) Fournit les arguments qui sont adoptés lorsque le DE appelle l’EE.

 [Interfaces d’évaluateur d’expression clés](../../extensibility/debugger/key-expression-evaluator-interfaces.md) Décrit les interfaces cruciales nécessaires lors de la rédaction d’un EE, ainsi que le contexte de l’évaluation.

## <a name="see-also"></a>Voir aussi
- [Rédaction d’un évaluateur d’expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Affichage des habitants](../../extensibility/debugger/displaying-locals.md)
- [Modification de la valeur d’un](../../extensibility/debugger/changing-the-value-of-a-local.md)
