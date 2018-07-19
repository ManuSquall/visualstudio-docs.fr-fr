---
title: Évaluation de l’expression (Kit de développement logiciel de débogage de Visual Studio) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 022a0ee21b7a58fdd69249b240490fc3c1df8361
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109803"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Évaluation de l’expression (Kit de développement logiciel de débogage de Visual Studio)
En mode arrêt, l’IDE doit être en mesure d’évaluer des expressions simples qui impliquent plusieurs variables de votre programme. Pour ce faire, le moteur de débogage (DE) doit être en mesure d’analyser et d’évaluer une expression qui est entrée dans une des fenêtres de l’IDE.  
  
 Les expressions sont créées à l’aide de la [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) (méthode) et sont représentées par résultant [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interface.  
  
 Le **IDebugExpression2** interface est implémentée par les appels DE son **EvalAsync** méthode pour retourner un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interface à l’IDE, afin d’afficher le résultats de l’évaluation d’expression dans l’IDE. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) retourne une structure qui peut être utilisée pour placer la valeur d’une expression dans une fenêtre Espion ou dans la fenêtre variables locales.  
  
 Le package ou la session de débogage Gestionnaire de débogage (SDM) appelle [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) ou [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) pour obtenir un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interface qui représente le résultat de l’évaluation. `IDebugProperty2` a des méthodes qui retournent le nom, le type et la valeur de l’expression. Ces informations s’affichent dans les différentes fenêtres du débogueur.  
  
## <a name="using-expression-evaluation"></a>L’évaluation d’Expression  
 Pour utiliser l’évaluation d’expression, vous devez implémenter la [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) (méthode) et toutes les méthodes de la [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) de l’interface, comme indiqué dans le tableau suivant.  
  
|Méthode|Description|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Évalue une expression de façon asynchrone.|  
|[Abandon](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Termine l’évaluation de l’expression asynchrone.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Évalue une expression de façon synchrone.|  
  
 Évaluation synchrone et asynchrone requièrent l’implémentation de la [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (méthode). Évaluation de l’expression asynchrone requiert l’implémentation de [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôle de l’exécution et évaluation de l’état](../../extensibility/debugger/execution-control-and-state-evaluation.md)