---
title: Évaluation de l’expression en Mode arrêt | Microsoft Docs
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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116223"
---
# <a name="expression-evaluation-in-break-mode"></a>Évaluation d’expression dans le mode arrêt
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La section suivante décrit le processus qui se produit lorsque le débogueur est en mode arrêt et procéder à l’évaluation de l’expression.  
  
## <a name="expression-evaluation-process"></a>Processus d’évaluation d’expression  
 Voici les étapes de base impliquées dans l’évaluation d’une expression :  
  
1. Appelle le Gestionnaire de session de débogage (SDM) [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) pour obtenir une interface de contexte d’expression, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2. Le SDM appelle ensuite [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) avec la chaîne à analyser.  
  
3. Si ParseText ne retourne pas S_OK, la raison de l’erreur est retournée.  
  
     -otherwise-  
  
     Si ParseText retourne S_OK, le SDM pouvez ensuite appeler [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) pour obtenir une valeur finale à partir de l’expression analysée.  
  
    - En cas d’utilisation `IDebugExpression2::EvaluateSync`, l’interface de rappel donné est utilisé pour communiquer le processus en cours de l’évaluation. La valeur finale est retournée dans un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interface.  
  
    - En cas d’utilisation `IDebugExpression2::EvaluateAsync`, l’interface de rappel donné est utilisé pour communiquer le processus en cours de l’évaluation. Une fois l’évaluation terminée, EvaluateAsync envoie un [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) interface via le rappel. Avec cette interface d’événement, la valeur finale peut être obtenue avec [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Événements d’appel du débogueur](../../extensibility/debugger/calling-debugger-events.md)
