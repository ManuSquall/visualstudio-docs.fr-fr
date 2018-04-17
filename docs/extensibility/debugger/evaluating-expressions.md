---
title: L’évaluation d’Expressions | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 47de275d63f5be1743408aa93c971dcff2959c25
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="evaluating-expressions"></a>L’évaluation des Expressions
Les expressions sont créées à partir de chaînes passés depuis l’automatique, Espion, Espion express ou immédiate. Lorsqu’une expression est évaluée, il génère une chaîne imprimable qui contient le nom et le type de variable ou argument et sa valeur. Cette chaîne est affichée dans la fenêtre IDE correspondante.  
  
## <a name="implementation"></a>Implémentation  
 Les expressions sont évaluées lorsqu’un programme s’est arrêté à un point d’arrêt. L’expression elle-même est représentée par une [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interface, qui représente une expression analysée est prête pour la liaison et d’évaluation dans le contexte de l’évaluation d’expression donnée. Le frame de pile détermine le contexte de d’évaluation d’expression, qui fournit par le moteur de débogage (Allemagne) en implémentant le [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface.  
  
 Une chaîne de l’utilisateur et un [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface, un moteur de débogage (DE) peut obtenir un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interface en passant la chaîne de l’utilisateur pour le [ IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) (méthode). L’interface IDebugExpression2 retournée contient l’expression analysée prête pour l’évaluation.  
  
 Avec la `IDebugExpression2` interface, le DE peut obtenir la valeur de l’expression à l’évaluation d’expression synchrone ou asynchrone, à l’aide de [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [IDebugExpression2 :: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Cette valeur, ainsi que le nom et le type de la variable ou un argument, est envoyée à l’IDE pour l’affichage. La valeur, le nom et le type sont représentées par une [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interface.  
  
 Pour activer l’évaluation d’expression, un DE doit implémenter la [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) et [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaces. Évaluation synchrone et asynchrone requièrent l’implémentation de la [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [Frames de pile](../../extensibility/debugger/stack-frames.md)   
 [Contexte d’évaluation d’expression](../../extensibility/debugger/expression-evaluation-context.md)   
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)