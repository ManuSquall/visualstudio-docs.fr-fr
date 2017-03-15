---
title: "L&#39;&#233;valuation des Expressions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "expressions (débogage SDK), l'évaluation"
  - "évaluation de l'expression [Debugging SDK], le débogage"
  - "évaluation d’expression"
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# L&#39;&#233;valuation des Expressions
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les expressions sont créées des chaînes passé vers le bas les automobiles, de l'affiche, de l'Espion Express, les fenêtres ou immédiates.  Lorsqu'une expression est évaluée, elle génère une chaîne imprimable qui contient le nom et le type de variable ou argument et sa valeur.  Cette chaîne est affichée dans la fenêtre correspondante de l'IDE.  
  
## Implémentation  
 Les expressions sont évaluées lorsqu'un programme a arrêté par un point d'arrêt.  L'expression elle\-même est représentée par une interface d' [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , qui représente une expression analysée qui est prête pour la liaison et évaluation dans le contexte donné d'évaluation de l'expression.  Le frame de pile détermine le contexte d'évaluation de l'expression, qui le \(DE\) fournit du moteur de débogage en implémentant l'interface d' [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) .  
  
 Étant donné un utilisateur la chaîne et une interface d' [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) , un moteur \(DE\) de débogage peut obtenir une interface d' [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) en passant la chaîne utilisateur à la méthode d' [IDebugExpressionContext2 : : ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) .  l'interface IDebugExpression2 retournée contient l'expression analysée prête pour l'évaluation.  
  
 Avec l'interface d' `IDebugExpression2` , le De peut obtenir la valeur de l'expression via l'évaluation d'une expression synchrone ou asynchrone, à l'aide de [IDebugExpression2 : : EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [IDebugExpression2 : : EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).  Cette valeur, avec le nom et le type de la variable ou de l'argument, est envoyé à l'IDE pour l'affichage.  La valeur, le nom, le type sont représentés par une interface d' [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) .  
  
 pour activer l'évaluation de l'expression, un De doit implémenter les interfaces d' [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) et d' [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) .  l'évaluation synchrone et asynchrone requièrent l'implémentation de la méthode d' [IDebugProperty2 : : GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) .  
  
## Voir aussi  
 [Frames de pile](../../extensibility/debugger/stack-frames.md)   
 [Contexte d'évaluation d'expression](../../extensibility/debugger/expression-evaluation-context.md)   
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)