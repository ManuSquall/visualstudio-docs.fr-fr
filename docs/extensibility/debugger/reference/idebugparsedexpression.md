---
title: IDebugParsedExpression | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugParsedExpression
helpviewer_keywords: IDebugParsedExpression interface
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e6ccaf11dc94702b29888a83c108908be3f8f354
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
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
  
## <a name="requirements"></a>Configuration requise  
 En-tête : ee.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)