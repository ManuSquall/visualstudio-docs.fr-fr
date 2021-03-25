---
title: Architecture de l’évaluateur d’expression | Microsoft Docs
description: En savoir plus sur l’intégration d’un langage propriétaire dans le package de débogage Visual Studio, y compris l’évaluateur d’expression et les interfaces de fournisseur de symboles/Binder.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 31b382f4765a115657fb213f39530e88e4008c95
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094729"
---
# <a name="expression-evaluator-architecture"></a>Architecture de l’évaluateur d’expression
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 L’intégration d’un langage propriétaire dans le package de débogage de Visual Studio signifie que vous devez configurer les interfaces d’évaluateur d’expression (EE) requises et appeler le fournisseur de symboles du Common Language Runtime (SP) et les interfaces de Binder. Les objets SP et Binder, ainsi que l’adresse d’exécution actuelle, sont le contexte dans lequel les expressions sont évaluées. Les informations que ces interfaces produisent et consomment représentent les concepts clés de l’architecture d’un EE.

## <a name="overview"></a>Vue d’ensemble

### <a name="parse-the-expression"></a>Analyser l’expression
 Lorsque vous déboguez un programme, les expressions sont évaluées pour plusieurs raisons, mais toujours lorsque le programme en cours de débogage a été arrêté à un point d’arrêt (point d’arrêt placé par l’utilisateur ou un point de rupture provoqué par une exception). C’est à ce moment-là que Visual Studio obtient un frame de pile, tel que représenté par l’interface [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) , à partir du moteur de débogage (de). Visual Studio appelle ensuite [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) pour accéder à l’interface [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) . Cette interface représente un contexte dans lequel les expressions peuvent être évaluées ; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) est le point d’entrée du processus d’évaluation. Jusqu’à présent, toutes les interfaces sont implémentées par le DE.

 Quand `IDebugExpressionContext2::ParseText` est appelé, le de instancie l’EE associé à la langue du fichier source où le point d’arrêt s’est produit (le de instancie également le SH à ce stade). EE est représenté par l’interface [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) . Le appelle ensuite [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) pour convertir l’expression (sous forme de texte) en expression analysée, prête pour l’évaluation. Cette expression analysée est représentée par l’interface [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) . L’expression est généralement analysée et n’est pas évaluée à ce stade.

 Le DE crée un objet qui implémente l’interface [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , place l' `IDebugParsedExpression` objet dans l' `IDebugExpression2` objet et retourne l' `IDebugExpression2` objet à partir de `IDebugExpressionContext2::ParseText` .

### <a name="evaluate-the-expression"></a>Évaluer l’expression
 Visual Studio appelle [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) pour évaluer l’expression analysée. Ces deux méthodes appellent [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) ( `IDebugExpression2::EvaluateSync` appelle immédiatement la méthode, tandis que `IDebugExpression2::EvaluateAsync` appelle la méthode via un thread d’arrière-plan) pour évaluer l’expression analysée et retourner une interface [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) qui représente la valeur et le type de l’expression analysée. `IDebugParsedExpression::EvaluateSync` utilise le SH, l’adresse et le Binder fournis pour convertir l’expression analysée en valeur réelle, représentée par l' `IDebugProperty2` interface.

### <a name="for-example"></a>Par exemple
 Une fois qu’un point d’arrêt a été atteint dans un programme en cours d’exécution, l’utilisateur choisit d’afficher une variable dans la boîte de dialogue **Espion express** . Cette boîte de dialogue affiche le nom de la variable, sa valeur et son type. L’utilisateur peut généralement modifier la valeur.

 Quand la boîte de dialogue **Espion express** s’affiche, le nom de la variable examinée est envoyé sous forme de texte à [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Cela retourne un objet [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) qui représente l’expression analysée, dans ce cas, la variable. [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) est ensuite appelé pour produire un `IDebugProperty2` objet qui représente la valeur et le type de la variable, ainsi que son nom. Il s’agit des informations qui s’affichent.

 Si l’utilisateur modifie la valeur de la variable, [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) est appelé avec la nouvelle valeur, qui modifie la valeur de la variable en mémoire afin qu’il soit utilisé lorsque le programme reprend son exécution.

 Pour plus d’informations sur ce processus d’affichage des valeurs des variables, consultez Affichage des variables [locales](../../extensibility/debugger/displaying-locals.md) . Consultez [modification de la valeur d’un local](../../extensibility/debugger/changing-the-value-of-a-local.md) pour plus d’informations sur la modification de la valeur d’une variable.

## <a name="in-this-section"></a>Dans cette section
 [Contexte d’évaluation](../../extensibility/debugger/evaluation-context.md) Fournit les arguments qui sont passés lorsque le DE l’appel à EE.

 [Interfaces d’évaluateur d’expression clés](../../extensibility/debugger/key-expression-evaluator-interfaces.md) Décrit les interfaces essentielles nécessaires à l’écriture d’un EE, ainsi que le contexte d’évaluation.

## <a name="see-also"></a>Voir aussi
- [Écriture d’un évaluateur d’expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Affichage des variables locales](../../extensibility/debugger/displaying-locals.md)
- [Modification de la valeur d’un local](../../extensibility/debugger/changing-the-value-of-a-local.md)
