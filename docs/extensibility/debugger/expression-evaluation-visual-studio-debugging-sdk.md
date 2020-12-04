---
title: Évaluation d’expression (kit de développement logiciel (SDK) de débogage Visual Studio) | Microsoft Docs
description: En mode arrêt, l’IDE évalue les expressions qui impliquent des variables de programme. Découvrez comment le moteur de débogage analyse et évalue une expression.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c398d9eb79a6b5fcd1a6851596ab8913faf32fa
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560887"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Évaluation d’expression (kit de développement logiciel (SDK) de débogage Visual Studio)
En mode arrêt, l’IDE doit évaluer des expressions simples impliquant plusieurs variables de programme. Pour effectuer son évaluation, le moteur de débogage (DE) doit analyser et évaluer une expression entrée dans l’une des fenêtres de l’IDE.

 Les expressions sont créées avec la méthode [IDebugExpressionContext2 ::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) et représentées par l’interface [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) résultante.

 L’interface **IDebugExpression2** est implémentée par le et appelle sa méthode **EvalAsync** pour retourner une interface [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) à l’IDE, afin d’afficher les résultats de l’évaluation de l’expression dans l’IDE. [IDebugProperty2 :: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) retourne une structure utilisée pour placer la valeur d’une expression dans une fenêtre **Espion** ou dans la fenêtre **variables locales** .

 Le package de débogage ou le gestionnaire de débogage de session (SDM) appelle [IDebugExpression2 :: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) ou [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) pour obtenir une interface [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) qui représente le résultat de l’évaluation. `IDebugProperty2` a des méthodes qui retournent le nom, le type et la valeur de l’expression. Ces informations s’affichent dans différentes fenêtres du débogueur.

## <a name="using-expression-evaluation"></a>Utilisation de l’évaluation d’expression
 Pour utiliser l’évaluation d’expression, vous devez implémenter la méthode [IDebugExpressionContext2 ::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) et toutes les méthodes de l’interface [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , comme indiqué dans le tableau suivant.

|Méthode|Description|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Évalue une expression de manière asynchrone.|
|[Abandon](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Termine l’évaluation de l’expression asynchrone.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Évalue une expression de façon synchrone.|

 L’évaluation synchrone et asynchrone requiert l’implémentation de la méthode [IDebugProperty2 :: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) . L’évaluation d’expression asynchrone requiert l’implémentation de [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).

## <a name="see-also"></a>Voir aussi
- [Contrôle d’exécution et évaluation de l’État](../../extensibility/debugger/execution-control-and-state-evaluation.md)
