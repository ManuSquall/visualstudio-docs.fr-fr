---
title: "Évaluation de l’expression en Mode arrêt | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: cd28633fcb4b8186dae154428e489d51041aa8b2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="expression-evaluation-in-break-mode"></a>Évaluation de l’expression en Mode arrêt
La liste suivante décrit le processus qui se produit lorsque le débogueur est en mode arrêt et qu’il doit effectuer l’évaluation de l’expression.  
  
## <a name="expression-evaluation-process"></a>Processus d’évaluation d’expression  
 Voici les étapes de base impliquées dans l’évaluation d’une expression :  
  
1.  Le Gestionnaire de session de débogage (SDM) appelle [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) pour obtenir une interface de contexte d’expression, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2.  Le SDM appelle ensuite [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) avec la chaîne à analyser.  
  
3.  Si ParseText ne retourne pas S_OK, la raison de l’erreur est retournée.  
  
     -dans le cas contraire-  
  
     Si ParseText retourne S_OK, le SDM peut appeler ensuite [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) pour obtenir une valeur finale de l’expression analysée.  
  
    -   En cas d’utilisation `IDebugExpression2::EvaluateSync`, l’interface de rappel donné est utilisé pour communiquer le processus en cours de l’évaluation. La valeur finale est retournée dans un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interface.  
  
    -   En cas d’utilisation `IDebugExpression2::EvaluateAsync`, l’interface de rappel donné est utilisé pour communiquer le processus en cours de l’évaluation. Une fois l’évaluation terminée, EvaluateAsync envoie un [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) interface via le rappel. Avec cette interface d’événement, la valeur finale peut être obtenue avec [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Événements d’appel du débogueur](../../extensibility/debugger/calling-debugger-events.md)