---
title: "IEEVisualizerService | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEVisualizerService"
helpviewer_keywords: 
  - "Interface de IEEVisualizerService"
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# IEEVisualizerService
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cette interface implémente des méthodes qui fournissent des fonctionnalités à la [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) et [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) interfaces.  
  
## Syntaxe  
  
```  
IEEVisualizerService : IUnknown  
```  
  
## Notes relatives à l'attention des implémenteurs  
 Visual Studio implémente cette interface pour permettre un évaluateur d’expression \(EE\) pour prendre en charge les visualiseurs de type.  
  
## Remarques pour les appelants  
 Les appels EE [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) pour obtenir cette interface dans le cadre de la prise en charge pour des visualiseurs de type.  
  
## Méthodes dans l’ordre Vtable  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|Récupère le nombre de visionneuses personnalisées sur lequel ce service connaît.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|Récupère la liste des visionneuses personnalisées.|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|Retourne un objet proxy pour une propriété.|  
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|Récupère le nombre de chaînes de valeur à afficher pour la propriété spécifiée ou un champ.|  
  
## Notes  
 L’IDE utilise le [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interface pour déterminer s’il existe des visionneuses personnalisées ou tapez visualiseurs pour la propriété. En créant un service de visualiseur \(avec [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)\), le EE peut fournir la fonctionnalité à le `IDebugProperty3` et [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) \(qui prend en charge affichage et modification d’une valeur de propriété\) des interfaces et ainsi prendre en charge les visualiseurs de type.  
  
 Si une EE possède des visionneuses personnalisées elle\-même implémente, la EE, ajoutez le `CLSID`s de ces visionneuses personnalisées à la fin de la liste renvoyée par [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md). Cela permet une EE prendre en charge les visualiseurs de type et ses propres visionneuses personnalisées. Assurez\-vous juste que [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md) reflète l’ajout de des visionneuses personnalisées.  
  
 Consultez [Visualiseur de type et de la visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) pour en savoir plus sur la différence entre les visualiseurs et les visionneuses.  
  
## Configuration requise  
 En\-tête : ee.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de l'évaluation d'expression](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)   
 [Visualiseur de type et de la visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)