---
title: Évaluation des expressions (en anglais) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18e342704cbb4abd7de9667576ce331ef8fbf60a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738831"
---
# <a name="evaluate-expressions"></a>Évaluer les expressions
Les expressions sont créées à partir de cordes transmises par les **Autos**, **Watch**, **QuickWatch,** ou **fenêtres immédiates.** Lorsqu’une expression est évaluée, elle génère une chaîne imprimable qui contient le nom et le type de variable ou d’argument et sa valeur. Cette chaîne est affichée dans la fenêtre IDE correspondante.

## <a name="implementation"></a>Implémentation
 Les expressions sont évaluées lorsqu’un programme s’arrête à un point d’arrêt. L’expression elle-même est représentée par une interface [IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) qui représente une expression analysée qui est prête pour la liaison et l’évaluation dans le contexte d’évaluation d’expression donnée. Le cadre de pile détermine le contexte d’évaluation d’expression, que le moteur de débogé (DE) fournit en mettant en œuvre [l’interface IDebugExpressionContext2.](../../extensibility/debugger/reference/idebugexpressioncontext2.md)

 Compte tenu d’une chaîne utilisateur et d’une interface [IDebugExpressionContext2,](../../extensibility/debugger/reference/idebugexpressioncontext2.md) un moteur de débogé (DE) peut obtenir une interface [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) en passant la chaîne utilisateur à la méthode [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) méthode. L’interface IDebugExpression2 qui est retournée contient l’expression analysée prête à être évaluation.

 Avec `IDebugExpression2` l’interface, le DE peut obtenir la valeur de l’expression par l’évaluation d’expression synchrone ou asynchrone, en utilisant [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Cette valeur, ainsi que le nom et le type de la variable ou de l’argumentation, est envoyé à l’IDE pour l’affichage. La valeur, le nom et le type sont représentés par une interface [IDebugProperty2.](../../extensibility/debugger/reference/idebugproperty2.md)

 Pour permettre l’évaluation de l’expression, un DE doit implémenter les interfaces [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) et [IDebugExpressionContext2.](../../extensibility/debugger/reference/idebugexpressioncontext2.md) L’évaluation synchrone et asynchrone exigent la mise en œuvre de la méthode [IDebugProperty2::GetPropertyInfo.](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)

## <a name="see-also"></a>Voir aussi
- [Piles de cadres](../../extensibility/debugger/stack-frames.md)
- [Contexte d’évaluation de l’expression](../../extensibility/debugger/expression-evaluation-context.md)
- [Tâches de débogé](../../extensibility/debugger/debugging-tasks.md)
