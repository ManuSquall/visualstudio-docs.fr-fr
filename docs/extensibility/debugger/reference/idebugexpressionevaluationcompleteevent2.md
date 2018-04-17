---
title: IDebugExpressionEvaluationCompleteEvent2 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7b57f59e3fbe0352229f64a2110e0c1e31e98012
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpressionevaluationcompleteevent2"></a>IDebugExpressionEvaluationCompleteEvent2
Cette interface est envoyée par le moteur de débogage (DE) pour le Gestionnaire de session de débogage (SDM) lors de l’évaluation de l’expression asynchrone est terminée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugExpressionEvaluationCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le D’implémente cette interface jusqu'à la fin du rapport d’une évaluation d’expression démarrée par un appel à [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface doit être implémentée sur le même objet que cette interface. Le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à la `IDebugEvent2` interface.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Le crée et envoie cet objet d’événement pour signaler la fin d’une évaluation d’expression. L’événement est envoyé à l’aide de la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fonction de rappel qui est fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugExpressionEvaluationCompleteEvent2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|Obtient l’expression d’origine.|  
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|Obtient le résultat de l’évaluation d’expression.|  
  
## <a name="remarks"></a>Notes  
 Le DE doit envoyer cet événement, si l’évaluation a réussi ou non.  
  
 Si l’évaluation n’a pas aboutie, le `DEBUG_PROPINFO_VALUE` et `DEBUG_PROPINFO_ATTRIB` indicateurs ne seront pas définis le [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) structure qui est retourné par [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (le [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objet est créé par le DE et retournée dans le `IDebugExpressionEvaluationCompleteEvent2` événement en cas d’échec de l’évaluation).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)