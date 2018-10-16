---
title: L’évaluation des Expressions | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b0aae7193c6840d389f7990f155fecb0149edc7f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49213679"
---
# <a name="evaluating-expressions"></a>Évaluation des expressions
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Expressions sont créées à partir de chaînes passées à partir de l’automatique, Espion, Espion express ou immédiates windows. Lorsqu’une expression est évaluée, il génère une chaîne imprimable qui contient le nom et le type de variable ou argument et sa valeur. Cette chaîne est affichée dans la fenêtre IDE correspondante.  
  
## <a name="implementation"></a>Implémentation  
 Les expressions sont évaluées lorsqu’un programme s’est arrêté à un point d’arrêt. L’expression elle-même est représentée par un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interface, qui représente une expression analysée est prête pour la liaison et d’évaluation dans le contexte de l’évaluation d’expression donnée. Le frame de pile détermine le contexte de d’évaluation d’expression, qui fournit par le moteur de débogage (dé) en implémentant le [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface.  
  
 Fonction d’une chaîne de l’utilisateur et un [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface, un moteur de débogage (dé) peut obtenir un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interface en passant la chaîne de l’utilisateur pour le [ IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) (méthode). L’interface IDebugExpression2 retournée contient l’expression analysée prête pour l’évaluation.  
  
 Avec le `IDebugExpression2` interface, l’Allemagne peut obtenir la valeur de l’expression par le biais d’évaluation d’expression synchrone ou asynchrone, à l’aide de [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [IDebugExpression2 :: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Cette valeur, ainsi que le nom et le type de la variable ou un argument, est envoyée à l’IDE pour l’affichage. La valeur, le nom et le type sont représentées par un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interface.  
  
 Pour activer l’évaluation d’expression, un dé doit implémenter le [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) et [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaces. Version d’évaluation à la fois synchrone et asynchrone requièrent l’implémentation de la [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [Frames de pile](../../extensibility/debugger/stack-frames.md)   
 [Contexte d’évaluation d’expression](../../extensibility/debugger/expression-evaluation-context.md)   
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)

