---
title: Architecture d’évaluateur d’expression | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da2f32cde96d7be482d0283510bcc3f0c127db9f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720677"
---
# <a name="expression-evaluator-architecture"></a>Architecture d’évaluateur d’expression
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 L’intégration d’un langage propriétaire dans Visual Studio à déboguer le package signifie que vous doit définir les interfaces d’évaluateur (EE) expression requis et appeler le fournisseur de symbole d’exécution commun language (SP) et des interfaces de classeur. Les objets SP et binder, ainsi que l’adresse de l’exécution en cours, sont le contexte dans lequel les expressions sont évaluées. Les informations que ces interfaces produisent et consomment représentent les concepts clés dans l’architecture d’un EE.

## <a name="overview"></a>Vue d'ensemble

### <a name="parse-the-expression"></a>Analyse de l’Expression
 Lorsque vous déboguez un programme, les expressions sont évaluées pour plusieurs raisons, mais toujours lorsque le programme en cours de débogage a été arrêté à un point d’arrêt (un point d’arrêt placée par l’utilisateur ou un provoquée par une exception). Il est pour l’instant lorsque Visual Studio obtient un frame de pile, telle que représentée par le [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interface, à partir de la (dé) du moteur de débogage. Visual Studio appelle ensuite [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) pour obtenir le [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface. Cette interface représente un contexte dans lequel les expressions peuvent être évaluées ; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) est le point d’entrée pour le processus d’évaluation. Jusqu'à présent, toutes les interfaces sont implémentées par l’Allemagne.

 Lorsque `IDebugExpressionContext2::ParseText` est appelée, l’Allemagne instancie le EE associé à la langue du fichier source où le point d’arrêt s’est produite (le D’instancie également le SH à ce stade). Le EE est représenté par le [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) interface. Le D’appelle ensuite [analyser](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) pour convertir l’expression (sous forme de texte) en une expression analysée, prêt pour l’évaluation. Cette expression analysée est représentée par le [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) interface. L’expression est analysée en général et pas évaluée à ce stade.

 Le DE crée un objet qui implémente le [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interface, met le `IDebugParsedExpression` de l’objet dans le `IDebugExpression2` objet et retourne le `IDebugExpression2` à partir de l’objet `IDebugExpressionContext2::ParseText`.

### <a name="evaluate-the-expression"></a>Évaluer l’expression
 Visual Studio appelle [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) pour évaluer l’expression analysée. Ces deux méthodes appellent [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (`IDebugExpression2::EvaluateSync` appelle la méthode immédiatement, tandis que `IDebugExpression2::EvaluateAsync` appelle la méthode via un thread d’arrière-plan) pour évaluer l’expression analysée et renvoyer un [ IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interface qui représente la valeur et le type de l’expression analysée. `IDebugParsedExpression::EvaluateSync` utilise le SH, l’adresse et le binder fourni pour convertir l’expression analysée en une valeur réelle, représentée par le `IDebugProperty2` interface.

### <a name="for-example"></a>Exemple :
 Après qu’un point d’arrêt est atteint dans un programme en cours d’exécution, l’utilisateur choisit d’afficher une variable dans le **Espion express** boîte de dialogue. Cette boîte de dialogue affiche le nom de la variable, sa valeur et son type. L’utilisateur peut modifier généralement la valeur.

 Lorsque le **Espion express** boîte de dialogue s’affiche, le nom de la variable en cours d’examen est envoyé sous forme de texte à [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Cette commande renvoie un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objet qui représente l’expression analysée, dans ce cas, la variable. [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) est ensuite appelée pour produire un `IDebugProperty2` objet qui représente la valeur de la variable et de type, ainsi que son nom. Il s’agit de ces informations s’affiche.

 Si l’utilisateur modifie la valeur de la variable, [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) est appelée avec la nouvelle valeur, ce qui modifie la valeur de la variable dans la mémoire, donc il sera utilisé lorsque le programme reprend en cours d’exécution.

 Consultez [variables locales affichage](../../extensibility/debugger/displaying-locals.md) pour plus d’informations sur ce processus d’afficher les valeurs des variables. Consultez [modification de la valeur d’une variable locale](../../extensibility/debugger/changing-the-value-of-a-local.md) pour plus d’informations sur la façon dont une valeur est modifiée.

## <a name="in-this-section"></a>Dans cette section
 [Contexte d’évaluation](../../extensibility/debugger/evaluation-context.md) fournit les arguments passés quand le D’appelle le EE.

 [Interfaces de d’évaluateur d’expression de clé](../../extensibility/debugger/key-expression-evaluator-interfaces.md) décrit les interfaces essentielles nécessaires lors de l’écriture d’un EE, ainsi que le contexte d’évaluation.

## <a name="see-also"></a>Voir aussi
- [Écriture d’un évaluateur d’expression de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Affichage des variables locales](../../extensibility/debugger/displaying-locals.md)
- [Modification de la valeur d’une variable locale](../../extensibility/debugger/changing-the-value-of-a-local.md)