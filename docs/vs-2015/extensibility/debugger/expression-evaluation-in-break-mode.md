---
title: Évaluation d’expression en mode arrêt | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 362e50e20519c358564d13ba169f706fe384ca5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152759"
---
# <a name="expression-evaluation-in-break-mode"></a>Évaluation d’expression dans le mode arrêt
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Les éléments suivants décrivent le processus qui se produit lorsque le débogueur est en mode arrêt et doit exécuter l’évaluation de l’expression.  
  
## <a name="expression-evaluation-process"></a>Processus d’évaluation d’expression  
 Voici les étapes de base impliquées dans l’évaluation d’une expression :  
  
1. Le gestionnaire de débogage de session (SDM) appelle [IDebugStackFrame2 :: GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) pour obtenir une interface de contexte d’expression, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2. Le SDM appelle ensuite [IDebugExpressionContext2 ::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) avec la chaîne à analyser.  
  
3. Si ParseText ne retourne pas S_OK, la raison de l’erreur est retournée.  
  
     dispose  
  
     Si ParseText retourne S_OK, le SDM peut ensuite appeler [IDebugExpression2 :: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [IDebugExpression2 :: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) pour obtenir une valeur finale de l’expression analysée.  
  
    - Dans le cas de l’utilisation de `IDebugExpression2::EvaluateSync` , l’interface de rappel donnée est utilisée pour communiquer le processus en cours de l’évaluation. La valeur finale est retournée dans une interface [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) .  
  
    - Dans le cas de l’utilisation de `IDebugExpression2::EvaluateAsync` , l’interface de rappel donnée est utilisée pour communiquer le processus en cours de l’évaluation. Une fois l’évaluation terminée, EvaluateAsync envoie une interface [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) via le rappel. Avec cette interface d’événement, la valeur finale peut être obtenue avec [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Événements d’appel du débogueur](../../extensibility/debugger/calling-debugger-events.md)
