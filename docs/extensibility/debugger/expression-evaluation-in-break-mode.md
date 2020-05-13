---
title: Évaluation de l’expression en mode pause (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc09fc43bd9f0edea4f6dc32e5f37c387c045796
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738723"
---
# <a name="expression-evaluation-in-break-mode"></a>Évaluation de l’expression en mode pause
La section suivante décrit le processus qui se produit lorsque le débbuggeur est en mode pause et doit effectuer une évaluation de l’expression.

## <a name="expression-evaluation-process"></a>Processus d’évaluation de l’expression
 Voici les étapes de base de l’évaluation d’une expression :

1. Le gestionnaire de déboque de session (SDM) appelle [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) pour obtenir une interface de contexte d’expression, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).

2. Le SDM appelle ensuite [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) avec la chaîne à analyser.

3. Si ParseText ne retourne pas S_OK, la raison de l’erreur est retournée.

     -sinon-

     Si ParseText ne retourne S_OK, le SDM peut alors appeler soit [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) pour obtenir une valeur finale de l’expression analysée.

    - Lors `IDebugExpression2::EvaluateSync`de l’utilisation, l’interface de rappel donnée communique le processus continu de l’évaluation. La valeur finale est retournée dans une interface [IDebugProperty2.](../../extensibility/debugger/reference/idebugproperty2.md)

    - Lors `IDebugExpression2::EvaluateAsync`de l’utilisation, l’interface de rappel donnée communique le processus continu de l’évaluation. Une fois l’évaluation terminée, EvaluateAsync envoie une interface [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) par le biais du rappel. Avec cette interface événement, la valeur finale se termine avec [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).

## <a name="see-also"></a>Voir aussi
- [Événements de débogénaire d’appel](../../extensibility/debugger/calling-debugger-events.md)
