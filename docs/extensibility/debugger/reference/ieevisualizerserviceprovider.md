---
title: "IEEVisualizerServiceProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerServiceProvider"
helpviewer_keywords: 
  - "Interface de IEEVisualizerServiceProvider"
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# IEEVisualizerServiceProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface permet d’accéder à une méthode qui peut créer un service de visualiseur, qui est utilisé pour gérer les tâches de visualiseur de type pour l’IDE.  
  
## Syntaxe  
  
```  
IEEVisualizerServiceProvider : IUnknown  
```  
  
## Notes relatives à l'attention des implémenteurs  
 Visual Studio implémente cette interface pour créer un objet de service de visualiseur, qui à son tour est utilisé pour fournir des ID de classe \(`CLSID`s\) des visualiseurs de type à l’IDE Visual Studio.  
  
## Remarques pour les appelants  
 L’évaluateur d’expression \(EE\) appelle [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) pour obtenir cette interface.  
  
## Méthodes dans l’ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Crée le service de visualiseur|  
  
## Notes  
 Le `IEEVisualizerServiceProvider` obtenue au cours de l’implémentation d’interface [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Le service de visualiseur qui crée cette interface est utilisé pour fournir des fonctionnalités à une [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interface le EE est responsable de l’implémentation. Le EE est également chargé d’implémenter un [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) interface qui permet des visualiseurs de type afficher et modifier la valeur d’une propriété.  
  
 Consultez [Visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md) Pour plus d’informations sur l’interagissent de ces interfaces.  
  
## Configuration requise  
 En\-tête : ee.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de l'évaluation d'expression](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [Visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md)