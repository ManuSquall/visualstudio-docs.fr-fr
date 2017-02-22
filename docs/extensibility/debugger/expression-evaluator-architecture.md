---
title: "Architecture d’&#233;valuateur d’expression | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "architecture, les évaluateurs d’expression"
  - "évaluateurs d’expression, architecture"
  - "débogage des évaluateurs d’expression [Debugging SDK],"
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Architecture d’&#233;valuateur d’expression
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Intégration d’un langage propriétaire dans le package de débogage Visual Studio signifie implémentant les interfaces d’évaluateur \(EE\) expression requise et l’appel du fournisseur de symbole d’exécution common language \(SP\) et les interfaces de classeur. Les objets SP et du classeur, ainsi que l’adresse en cours d’exécution, sont le contexte dans lequel les expressions sont évaluées. Les informations que ces interfaces produisent et consomment représentent les concepts clés dans l’architecture d’un EE.  
  
## Vue d'ensemble  
  
### L’analyse de l’Expression  
 Lorsque vous déboguez un programme, les expressions sont évaluées pour plusieurs raisons, mais toujours lorsque le programme débogué a été arrêté à un point d’arrêt \(un point d’arrêt placé par l’utilisateur ou un provoquées par une exception\). Il est à ce moment lorsque Visual Studio obtient un frame de pile, tel que représenté par la [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interface, à partir du moteur de débogage \(DE\). Visual Studio appelle ensuite [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) pour obtenir le [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface. Cette interface représente un contexte dans lequel les expressions peuvent être évaluées ; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) est le point d’entrée pour le processus d’évaluation. Jusqu'à présent, toutes les interfaces sont implémentées par le DE.  
  
 Lorsque `IDebugExpressionContext2::ParseText` est appelé, le D’instancie le EE associé à la langue du fichier source où le point d’arrêt s’est produite \(le D’instancie également le SH à ce stade\). Le EE est représenté par la [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) interface. Le D’appelle ensuite [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) pour convertir l’expression \(sous forme de texte\) dans une expression analysée, prêt pour l’évaluation. Cette expression analysée est représentée par la [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) interface. Notez que l’expression est analysée en général pas évaluée à ce stade.  
  
 Le DE crée un objet qui implémente le [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interface met le `IDebugParsedExpression` de l’objet dans le `IDebugExpression2` objet et retourne le `IDebugExpression2` à partir de l’objet `IDebugExpressionContext2::ParseText`.  
  
### Évaluation de l’Expression  
 Visual Studio appelle [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) pour évaluer l’expression analysée. Ces deux méthodes appellent [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) \(`IDebugExpression2::EvaluateSync` appelle la méthode immédiatement, tandis que `IDebugExpression2::EvaluateAsync` appelle la méthode via un thread d’arrière\-plan\) pour évaluer l’expression analysée et renvoyer un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interface qui représente la valeur et le type de l’expression analysée.`IDebugParsedExpression::EvaluateSync` utilise SH, l’adresse et le binder fourni pour convertir l’expression analysée en une valeur réelle, représentée par le `IDebugProperty2` interface.  
  
### Par exemple  
 Après qu’un point d’arrêt est atteint dans un programme en cours d’exécution, l’utilisateur choisit d’afficher une variable dans le **Espion express** boîte de dialogue. Cette boîte de dialogue affiche le nom de la variable, sa valeur et son type. L’utilisateur peut modifier généralement la valeur.  
  
 Lors de la **Espion express** boîte de dialogue s’affiche, le nom de la variable en cours d’examen est envoyé sous forme de texte à [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Cette opération retourne un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objet qui représente l’expression analysée, dans ce cas, la variable.[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) est ensuite appelé pour produire un `IDebugProperty2` objet qui représente la valeur de la variable et type, ainsi que son nom. Il s’agit de ces informations s’affiche.  
  
 Si l’utilisateur modifie la valeur de la variable, [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) est appelée avec la nouvelle valeur, ce qui modifie la valeur de la variable dans la mémoire, donc il sera utilisé lorsque le programme reprend en cours d’exécution.  
  
 Consultez [Afficher les variables locales](../../extensibility/debugger/displaying-locals.md) Pour plus d’informations sur ce processus d’afficher les valeurs des variables. Consultez [Modification de la valeur des variables locales](../../extensibility/debugger/changing-the-value-of-a-local.md) Pour plus d’informations sur la façon dont la valeur d’une variable est modifiée.  
  
## Dans cette section  
 [Contexte d’évaluation](../../extensibility/debugger/evaluation-context.md)  
 Fournit les arguments qui sont passés lorsque le D’appelle le EE.  
  
 [Interfaces d’évaluateur d’Expression clé](../../extensibility/debugger/key-expression-evaluator-interfaces.md)  
 Décrit les interfaces essentielles nécessaires lors de l’écriture d’un EE, ainsi que le contexte d’évaluation.  
  
## Voir aussi  
 [Écriture d'un évaluateur d'Expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Afficher les variables locales](../../extensibility/debugger/displaying-locals.md)   
 [Modification de la valeur des variables locales](../../extensibility/debugger/changing-the-value-of-a-local.md)