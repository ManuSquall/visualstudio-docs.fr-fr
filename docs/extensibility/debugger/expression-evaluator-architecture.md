---
title: "Architecture d’évaluateur d’expression | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6805b97da8e8f742b1b6c0bb3298e9324bb1f72e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="expression-evaluator-architecture"></a>Architecture d’évaluateur d’expression
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Intégration d’un langage propriétaire dans le package de débogage Visual Studio signifie implémentant les interfaces d’évaluateur (Java EE) expression requis et l’appel du fournisseur de symbole d’exécution de langage commun (SP) et les interfaces de classeurs. Les objets SP et le classeur, ainsi que l’adresse de l’exécution en cours, sont le contexte dans lequel les expressions sont évaluées. Les informations que ces interfaces créent et consomment représentent les concepts clés dans l’architecture d’un EE.  
  
## <a name="overview"></a>Vue d'ensemble  
  
### <a name="parsing-the-expression"></a>Analyse de l’Expression  
 Lorsque vous déboguez un programme, les expressions sont évaluées pendant un nombre de raisons, mais toujours lorsque le programme débogué a été arrêté à un point d’arrêt (un point d’arrêt placée par l’utilisateur ou un provoquée par une exception). Il est en cours de lorsque Visual Studio obtient un frame de pile, tel que représenté par la [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interface, à partir du moteur de débogage (DE). Visual Studio appelle ensuite [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) pour obtenir le [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface. Cette interface représente un contexte dans lequel les expressions peuvent être évaluées ; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) est le point d’entrée pour le processus d’évaluation. Jusqu'à présent, toutes les interfaces sont implémentées par le DE.  
  
 Lorsque `IDebugExpressionContext2::ParseText` est appelée, le D’instancie le EE associé à la langue du fichier source où le point d’arrêt s’est produite (le DE également instancie le SH à ce stade). Le EE est représenté par le [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) interface. Le D’appelle ensuite [analyser](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) pour convertir l’expression (sous forme de texte) dans une expression analysée, prêt pour l’évaluation. Cette expression analysée est représentée par le [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) interface. Notez que l’expression est analysée en général pas évaluée à ce stade.  
  
 Le DE crée un objet qui implémente le [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interface, met la `IDebugParsedExpression` de l’objet dans le `IDebugExpression2` objet et retourne le `IDebugExpression2` à partir de l’objet `IDebugExpressionContext2::ParseText`.  
  
### <a name="evaluating-the-expression"></a>Évaluation de l’Expression  
 Visual Studio appelle [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) pour évaluer l’expression analysée. Ces deux méthodes appellent [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (`IDebugExpression2::EvaluateSync` appelle la méthode immédiatement, tandis que `IDebugExpression2::EvaluateAsync` appelle la méthode via un thread d’arrière-plan) pour évaluer l’expression analysée et renvoyer un [ IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interface qui représente la valeur et le type de l’expression analysée. `IDebugParsedExpression::EvaluateSync`utilise SH, l’adresse et le classeur fourni pour convertir l’expression analysée une valeur réelle, représentée par le `IDebugProperty2` interface.  
  
### <a name="for-example"></a>Par exemple  
 Après qu’un point d’arrêt est atteint dans un programme en cours d’exécution, l’utilisateur choisit afficher une variable dans le **Espion express** boîte de dialogue. Cette boîte de dialogue affiche le nom de la variable, sa valeur et son type. L’utilisateur peut modifier généralement la valeur.  
  
 Lorsque le **Espion express** boîte de dialogue s’affiche, le nom de la variable en cours d’examen est envoyé sous forme de texte à [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Cette opération retourne un [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objet qui représente l’expression analysée, dans ce cas, la variable. [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) est alors appelée pour produire un `IDebugProperty2` objet qui représente la valeur de la variable et de type, ainsi que son nom. Il s’agit de ces informations s’affiche.  
  
 Si l’utilisateur modifie la valeur de la variable, [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) est appelée avec la nouvelle valeur, ce qui modifie la valeur de la variable dans la mémoire, donc il sera utilisé lorsque le programme reprend en cours d’exécution.  
  
 Consultez [afficher les variables locales](../../extensibility/debugger/displaying-locals.md) pour plus d’informations sur ce processus d’afficher les valeurs des variables. Consultez [modification de la valeur des variables locales](../../extensibility/debugger/changing-the-value-of-a-local.md) pour plus d’informations sur la façon dont la valeur d’une variable est modifiée.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Contexte d’évaluation](../../extensibility/debugger/evaluation-context.md)  
 Fournit les arguments qui sont passées au moment de la D’appelle le Java EE.  
  
 [Interfaces d’évaluateur d’expression clé](../../extensibility/debugger/key-expression-evaluator-interfaces.md)  
 Décrit les interfaces cruciales nécessaires lors de l’écriture d’un EE, ainsi que le contexte d’évaluation.  
  
## <a name="see-also"></a>Voir aussi  
 [L’écriture d’un évaluateur d’Expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Affichage des variables locales](../../extensibility/debugger/displaying-locals.md)   
 [Modification de la valeur d’une variable locale](../../extensibility/debugger/changing-the-value-of-a-local.md)