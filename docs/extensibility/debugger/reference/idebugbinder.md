---
title: IDebugBinder | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder
helpviewer_keywords: IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f3377ade8cc4301e1d8a5be19c5d828755934ce9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression managé](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface est liée à un champ de symbole, généralement retourné par le fournisseur de symboles, à un contexte de la mémoire ou un objet qui contient la valeur actuelle du symbole.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugBinder : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Cette interface prend en charge d’évaluation d’expression et doit être implémentée par le moteur de débogage (DE).  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Cette interface est utilisée dans le processus d’évaluation d’expression et est généralement utilisée dans l’implémentation de [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) et [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugBinder`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Lier](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Obtient le contexte de la mémoire ou l’objet qui contient la valeur actuelle du symbole.|  
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Détermine le type au moment de l’exécution d’un objet.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Convertit une adresse mémoire ou emplacement d’objet à un contexte de la mémoire.|  
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Obtient un [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) objet utilisé pour créer des paramètres de fonction.|  
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Obtient le type exact d’une variable.|  
  
## <a name="remarks"></a>Notes  
 Cette interface retourne les objets qui sont utilisés par l’évaluateur d’expression dans les arborescences d’analyse. L’évaluateur d’expression analyse une expression à l’aide du fournisseur de symbole pour convertir les symboles dans l’expression à des instances de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), qui décrivent chaque symbole en termes de son type et son emplacement dans le code source. Le [lier](../../../extensibility/debugger/reference/idebugbinder-bind.md) méthode convertit `IDebugField` objets [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) les objets qui se connectent ou lier un symbole de type à une valeur réelle de la mémoire. Ces `IDebugObject` sont ensuite stockés dans une arborescence d’analyse pour une évaluation ultérieure.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : ee.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de l’évaluation d’expression](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)