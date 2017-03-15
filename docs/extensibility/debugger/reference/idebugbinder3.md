---
title: "IDebugBinder3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder3"
helpviewer_keywords: 
  - "Interface de IDebugBinder3"
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugBinder3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface fournit l’accès aux types, les alias et les services de visualiseur personnalisé.  
  
## Syntaxe  
  
```  
IDebugBinder3 : IDebugBinder  
```  
  
## Notes relatives à l'attention des implémenteurs  
 Un moteur de débogage implémente cette interface pour prendre en charge les alias, les services de visualiseur personnalisé et l’accès aux informations de type d’objet.  
  
## Remarques pour les appelants  
 Un [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interface obtient cette interface à l’aide de [QueryInterface](/visual-cpp/atl/queryinterface).  
  
## Méthodes dans l’ordre Vtable  
 Outre les méthodes fournies par le [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interface, cette interface implémente les éléments suivants :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|Récupère un objet mémoire qui représente la mémoire à laquelle cet objet est lié.|  
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|Récupère l’exception associée à cet objet \(le cas échéant\),|  
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|Récupère un alias donné son nom,|  
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|Récupère un tableau de tous les alias pour cet objet,|  
|[GetTypeArgumentCount](../Topic/IDebugBinder3::GetTypeArgumentCount.md)|Obtient le nombre de types d’arguments associé à cet objet,|  
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|Récupère une liste de types d’arguments associé à cet objet,|  
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|Obtient une interface à un service de visualiseur|  
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|Convertit un emplacement de l’objet ou une adresse mémoire de 64 bits à un contexte de la mémoire.|  
  
## Configuration requise  
 En\-tête : ee.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de l'évaluation d'expression](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)