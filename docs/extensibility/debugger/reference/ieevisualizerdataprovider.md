---
title: "IEEVisualizerDataProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerDataProvider"
helpviewer_keywords: 
  - "Interface de IEEVisualizerDataProvider"
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IEEVisualizerDataProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface offre la possibilité de modifier la valeur d’un objet via un visualiseur de type.  
  
## Syntaxe  
  
```  
IEEVisualizerDataProvider : IUnknown  
```  
  
## Notes relatives à l'attention des implémenteurs  
 L’évaluateur d’expression implémente cette interface pour prendre en charge la modification des données sur un objet de propriété via un visualiseur de type.  
  
## Remarques pour les appelants  
 Cette interface est utilisée pour la création du [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) objet via un appel à [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Pour plus d'informations, consultez [Visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md).  
  
## Méthodes dans l’ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[CanSetObjectForVisualizer](../Topic/IEEVisualizerDataProvider::CanSetObjectForVisualizer.md)|Détermine s’il est possible de mettre à jour l’objet \(et par la suite, sa valeur\) qui est représentant ce visualiseur.|  
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Force une réévaluation de l’objet pour ce visualiseur.|  
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Obtient un objet existant de ce visualiseur \(aucune évaluation ne terminée\).|  
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Met à jour l’objet de ce visualiseur, modifiant ainsi la valeur que présente le visualiseur.|  
  
## Notes  
 Le service de visualiseur \(tel que représenté par le [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) de l’interface et retournée par [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)\) conserve une référence à l’objet implémentant le `IEEVisualizerDataProvider` interface. Par conséquent, le `IEEVisualizerDataProvider` interface ne doit pas être implémentée sur le même objet qui implémente le [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) Si cet objet conserve une référence à la `IEEVisualizerService` objet : entraîne une référence circulaire et un blocage se produit lorsque les objets sont détruits. L’approche recommandée consiste à implémenter `IEEVisualizerDataProvider` sur un objet distinct dans lequel les `IDebugProperty2` sans appeler les délégués de l’objet `IUnknown::AddRef` dessus.  
  
## Configuration requise  
 En\-tête : ee.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de l'évaluation d'expression](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [Visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md)