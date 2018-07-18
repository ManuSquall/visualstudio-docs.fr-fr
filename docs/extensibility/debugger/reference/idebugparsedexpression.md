---
title: IDebugParsedExpression | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugParsedExpression
helpviewer_keywords:
- IDebugParsedExpression interface
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8b877dd974a0b96a176b54f308a6317e7324b6ab
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122312"
---
# <a name="idebugparsedexpression"></a>IDebugParsedExpression
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface représente une expression analysée prête à être évaluée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugParsedExpression : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Évaluateur d’expression implémente cette interface pour représenter une expression analysée est prête pour l’évaluation.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Un appel à [analyser](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) retourne cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente la méthode de `IDebugParsedExpression`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|Évalue l’expression analysée.|  
  
## <a name="remarks"></a>Notes  
 Lorsque l’appelant est prêt pour évaluer l’expression, il appelle [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) pour retourner une [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui contient le résultat de l’évaluation. Cette approche en deux parties de l’évaluation, l’analyse, puis l’évaluation, permet à l’expression analysée être évaluées plusieurs fois, en ignorant le processus de longue durée de l’analyse de l’expression.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : ee.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)