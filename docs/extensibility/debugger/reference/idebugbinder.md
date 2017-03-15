---
title: "IDebugBinder | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder"
helpviewer_keywords: 
  - "Interface de IDebugBinder"
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# IDebugBinder
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface lie un champ de symbole, généralement retourné par le fournisseur de symboles, à un contexte de mémoire ou un objet qui contient la valeur actuelle du symbole.  
  
## Syntaxe  
  
```  
IDebugBinder : IUnknown  
```  
  
## Notes relatives à l'attention des implémenteurs  
 Cette interface prend en charge la version d’évaluation de l’expression et doit être implémentée par le moteur de débogage \(DE\).  
  
## Remarques pour les appelants  
 Cette interface est utilisée dans le processus d’évaluation d’expression et est généralement utilisée dans l’implémentation de [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) et [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).  
  
## Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugBinder`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Lier](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Obtient le contexte de la mémoire ou l’objet qui contient la valeur actuelle du symbole.|  
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Détermine le type au moment de l’exécution d’un objet.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Convertit une adresse mémoire ou emplacement d’objet à un contexte de la mémoire.|  
|[GetFunctionObject](../Topic/IDebugBinder::GetFunctionObject.md)|Obtient un [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) objet utilisé pour créer des paramètres de fonction.|  
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Obtient le type exact d’une variable.|  
  
## Notes  
 Cette interface retourne des objets qui sont utilisées par l’évaluateur d’expression en arborescences d’analyse. L’évaluateur d’expression analyse l’expression en utilisant le fournisseur de symboles pour convertir les symboles dans l’expression aux instances de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), qui décrivent chaque symbole en termes de son type et son emplacement dans le code source. Le [Lier](../../../extensibility/debugger/reference/idebugbinder-bind.md) méthode convertit `IDebugField` objets [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) les objets qui se connectent ou lier un symbole de type en une valeur réelle dans la mémoire. Ces `IDebugObject` objets sont ensuite stockés dans une arborescence d’analyse pour une évaluation ultérieure.  
  
## Configuration requise  
 En\-tête : ee.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de l'évaluation d'expression](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)