---
title: IDebugParsedExpression | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugParsedExpression
helpviewer_keywords:
- IDebugParsedExpression interface
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4aa7733dee79d60a2cc09123bc22ccb587f82cb9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765611"
---
# <a name="idebugparsedexpression"></a>IDebugParsedExpression
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface représente une expression analysée prête à être évaluée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugParsedExpression : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Un évaluateur d’expression implémente cette interface pour représenter une expression analysée est prête pour l’évaluation.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Un appel à [analyser](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) retourne cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente la méthode de `IDebugParsedExpression`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|Évalue l’expression analysée.|  
  
## <a name="remarks"></a>Notes  
 Lorsque l’appelant est prêt à évaluer l’expression, il appelle [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) pour retourner un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui contient le résultat de l’évaluation. Cette approche en deux parties pour évaluation, l’analyse puis évaluez, permet à l’expression analysée être évaluées plusieurs fois, en contournant le processus fastidieux de l’analyse de l’expression.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : ee.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)

