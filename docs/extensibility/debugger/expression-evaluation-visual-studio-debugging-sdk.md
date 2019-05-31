---
title: Évaluation de l’expression (Kit de développement logiciel de débogage de Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e1e09f2302a6bb8401dd8c9f2d7c48810d5ecdc
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353826"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Évaluation des expressions (débogage SDK Visual Studio)
En mode arrêt, l’IDE doit évaluer les expressions simples impliquant plusieurs variables de programme. Pour accomplir son évaluation, le moteur de débogage (dé) doit analyser et évaluer une expression qui est entrée dans une des fenêtres de l’IDE.

 Les expressions sont créées avec le [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) méthode et représenté par résultant [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interface.

 Le **IDebugExpression2** interface est implémentée par les appels DE son **EvalAsync** méthode pour retourner un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interface à l’IDE, afin d’afficher le résultats de l’évaluation d’expression dans l’IDE. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) retourne une structure qui est utilisée pour placer la valeur d’une expression dans une **espion** fenêtre ou dans le **variables locales** fenêtre.

 Le package ou la session de débogage Gestionnaire de débogage (SDM) appelle [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) ou [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) pour obtenir un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interface qui représente le résultat de l’évaluation. `IDebugProperty2` a des méthodes qui retournent le nom, le type et la valeur de l’expression. Ces informations s’affichent dans les différentes fenêtres du débogueur.

## <a name="using-expression-evaluation"></a>Avec l’évaluation d’expression
 Pour utiliser la version d’évaluation de l’expression, vous devez implémenter le [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) (méthode) et toutes les méthodes de la [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interface, comme indiqué dans le tableau suivant.

|Méthode|Description|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Évalue une expression de façon asynchrone.|
|[Abort](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Termine l’évaluation de l’expression asynchrone.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Évalue une expression de façon synchrone.|

 Évaluation synchrone et asynchrone requièrent l’implémentation de la [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (méthode). Évaluation des expressions asynchrones nécessite l’implémentation de [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).

## <a name="see-also"></a>Voir aussi
- [Évaluation de contrôle et l’état d’exécution](../../extensibility/debugger/execution-control-and-state-evaluation.md)