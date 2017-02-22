---
title: "L’impl&#233;mentation de Type visualiseurs et les visionneuses personnalis&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "débogage de visionneuse personnalisée [Debugging SDK],"
  - "visualiseur de type débogage [Debugging SDK],"
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# L’impl&#233;mentation de Type visualiseurs et les visionneuses personnalis&#233;es
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Dans Visual Studio 2015, ce moyen d’implémenter des évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateurs d’Expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple d’évaluateur d’Expression gérés](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Type visualiseurs et les visionneuses personnalisées autoriser un utilisateur à afficher les données d’un type particulier d’une manière plus explicite qu’un vidage hexadécimal simple de nombres. Un évaluateur d’expression \(EE\) peut associer des visionneuses personnalisées à des types de données ou des variables. Ces visionneuses personnalisées sont implémentés par le EE. Le EE peut prennent également en charge les visualiseurs de type externe, ce qui peuvent provenir d’un autre fournisseur tiers ou même l’utilisateur final.  
  
## Discussion  
  
### Visualiseurs de type  
 Visual Studio vous demande pour une liste de visualiseurs de type et les visionneuses personnalisées pour chaque objet à afficher dans une fenêtre Espion. Un évaluateur d’expression \(EE\) fournit cette liste pour chaque type pour lequel il souhaite prendre en charge les visualiseurs de type et les visionneuses personnalisées. Les appels à [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md) et [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) Démarrer l’ensemble du processus d’accéder aux visualiseurs de type et les visionneuses personnalisées \(voir [Visualisation et affichage des données](../../extensibility/debugger/visualizing-and-viewing-data.md) Pour plus d’informations sur la séquence d’appel\).  
  
### Visionneuses personnalisées  
 Les visionneuses personnalisées sont implémentés dans le EE pour un type de données et sont représentés par le [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) interface. Une visionneuse personnalisée n’est pas aussi flexible qu’un visualiseur de type, dans la mesure où elle est disponible uniquement lorsque le EE qui implémente cette visionneuse personnalisée particulière est en cours d’exécution. L’implémentation d’une visionneuse personnalisée est plus simple que celle prise en charge des visualiseurs de type. Toutefois, prenant en charge les visualiseurs de type flexibilité maximale pour l’utilisateur final pour visualiser ses données. Le reste de cet article concerne uniquement les visualiseurs de type.  
  
## Interfaces  
 Le EE implémente les interfaces suivantes pour prendre en charge les visualiseurs de type, à être utilisés par Visual Studio :  
  
-   [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)  
  
-   [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)  
  
-   [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)  
  
-   [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)  
  
-   [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
 Le EE consomme les interfaces suivantes pour prendre en charge les visualiseurs de type :  
  
-   [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)  
  
-   [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)  
  
-   [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)  
  
## Voir aussi  
 [Écriture d'un évaluateur d'Expression CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualisation et affichage des données](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)