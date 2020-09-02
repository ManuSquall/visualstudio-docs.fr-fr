---
title: Évaluation des expressions | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caff42c2e203151c6bab7d50b41744c2469ab3c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151623"
---
# <a name="evaluating-expressions"></a>Évaluation des expressions
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Les expressions sont créées à partir de chaînes transmises à partir des fenêtres automatique, espion, espion Express ou immédiat. Lorsqu’une expression est évaluée, elle génère une chaîne imprimable qui contient le nom et le type de variable ou d’argument et sa valeur. Cette chaîne s’affiche dans la fenêtre IDE correspondante.  
  
## <a name="implementation"></a>Implémentation  
 Les expressions sont évaluées lorsqu’un programme s’est arrêté à un point d’arrêt. L’expression elle-même est représentée par une interface [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , qui représente une expression analysée qui est prête pour la liaison et l’évaluation dans le contexte d’évaluation de l’expression donné. Le frame DE pile détermine le contexte d’évaluation d’expression, fourni par le moteur DE débogage en implémentant l’interface [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) .  
  
 Étant donné une chaîne utilisateur et une interface [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) , un moteur de débogage (de) peut obtenir une interface [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) en passant la chaîne utilisateur à la méthode [IDebugExpressionContext2 ::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) . L’interface IDebugExpression2 retournée contient l’expression analysée prête pour l’évaluation.  
  
 Avec l' `IDebugExpression2` interface, le peut récupérer la valeur de l’expression par le biais de l’évaluation d’expression synchrone ou asynchrone, à l’aide de [IDebugExpression2 :: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [IDebugExpression2 :: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Cette valeur, ainsi que le nom et le type de la variable ou de l’argument, sont envoyés à l’environnement de développement intégré (IDE) pour l’affichage. La valeur, le nom et le type sont représentés par une interface [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) .  
  
 Pour activer l’évaluation d’expression, un DE doit implémenter les interfaces [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) et [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) . Les évaluations synchrones et asynchrones requièrent l’implémentation de la méthode [IDebugProperty2 :: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [Frames de pile](../../extensibility/debugger/stack-frames.md)   
 [Contexte d’évaluation de l’expression](../../extensibility/debugger/expression-evaluation-context.md)   
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)
