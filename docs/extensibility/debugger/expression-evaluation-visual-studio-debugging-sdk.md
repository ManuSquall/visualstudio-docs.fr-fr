---
title: Évaluation de l’expression (Visual Studio Debugging SDK) Microsoft Docs
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
ms.openlocfilehash: e41179fd530818f5ac59aa54420ede1b4eafa1ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738711"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Évaluation de l’expression (Visual Studio Debugging SDK)
Pendant le mode pause, l’IDE doit évaluer les expressions simples impliquant plusieurs variables du programme. Pour réaliser son évaluation, le moteur de débogé (DE) doit analyser et évaluer une expression entrée dans l’une des fenêtres de l’IDE.

 Les expressions sont créées avec la méthode [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) et représentées par l’interface [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) qui en résulte.

 **L’interface IDebugExpression2** est mise en œuvre par le DE et appelle sa méthode **EvalAsync** pour retourner une interface [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) à l’IDE, afin d’afficher les résultats de l’évaluation d’expression dans l’IDE. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) retourne une structure qui est utilisée pour mettre la valeur d’une expression dans une fenêtre **de montre** ou dans la fenêtre **des sections locales.**

 Le package de débaillement ou gestionnaire de débbug session (SDM) appelle [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) ou [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) pour obtenir une interface [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) qui représente le résultat de l’évaluation. `IDebugProperty2`a des méthodes qui renvoient le nom, le type et la valeur de l’expression. Cette information apparaît dans diverses fenêtres de débaillement.

## <a name="using-expression-evaluation"></a>Utilisation de l’évaluation de l’expression
 Pour utiliser l’évaluation de l’expression, vous devez implémenter la méthode [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) et toutes les méthodes de l’interface [IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) comme indiqué dans le tableau suivant.

|Méthode|Description|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Évalue une expression asynchrone.|
|[Annuler](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Termine l’évaluation asynchrone d’expression.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Évalue une expression de façon synchrone.|

 L’évaluation synchrone et asynchrone nécessitent la mise en œuvre de la méthode [IDebugProperty2::GetPropertyInfo.](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) L’évaluation d’expression asynchrone nécessite la mise en œuvre de [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).

## <a name="see-also"></a>Voir aussi
- [Contrôle des exécutions et évaluation de l’État](../../extensibility/debugger/execution-control-and-state-evaluation.md)
