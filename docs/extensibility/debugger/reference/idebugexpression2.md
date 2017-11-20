---
title: IDebugExpression2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExpression2
helpviewer_keywords: IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5ba89642b51d4b1d471bc6c46d84441c6383005c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugexpression2"></a>IDebugExpression2
Cette interface représente un prêt de l’expression analysée pour la liaison et l’évaluation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugExpression2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur de débogage (DE) implémente cette interface pour représenter une expression analysée prête à être évaluée.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Un appel à [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) retourne cette interface. [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) retourne le [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface. Ces interfaces sont accessibles uniquement lorsque le programme en cours de débogage a été interrompu et un frame de pile n’est disponible.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugExpression2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Évalue cette expression de façon asynchrone.|  
|[Abandon](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Termine l’évaluation de l’expression asynchrone.|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Évalue cette expression de façon synchrone.|  
  
## <a name="remarks"></a>Remarques  
 Lorsqu’un programme s’est arrêté, le Gestionnaire de session de débogage (SDM) Obtient un frame de pile de la DE avec un appel à [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Le SDM appelle ensuite [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) pour obtenir le [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface. Il est suivi par un appel à [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) pour créer le `IDebugExpression2` interface qui représente l’expression analysée prête à être évaluée.  
  
 Appelle le SDM [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) pour évaluer l’expression et produire une valeur.  
  
 Dans une implémentation de `IDebugExpressionContext2::ParseText`, le D’utilise COM `CoCreateInstance` fonction pour instancier un évaluateur d’expression et obtenir un [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) interface (voir l’exemple dans le `IDebugExpressionEvaluator` interface). Le D’appelle ensuite [analyser](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) pour obtenir un [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) interface. Cette interface est utilisée dans l’implémentation de `IDebugExpression2::EvaluateSync` et `IDebugExpression2::EvaluateAsync` pour effectuer l’évaluation.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)