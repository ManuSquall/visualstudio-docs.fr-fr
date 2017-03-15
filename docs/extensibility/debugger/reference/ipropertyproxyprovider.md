---
title: "IPropertyProxyProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IPropertyProxyProvider"
helpviewer_keywords: 
  - "Interface de IPropertyProxyProvider"
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IPropertyProxyProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette interface fournit une interface de proxy pour afficher et modifier les données d'un objet.  
  
## Syntaxe  
  
```  
IPropertyProxyProvider : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 L'évaluateur \(EE\) d'expression implémente cette interface sur le même objet qui implémente l'interface d' [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) dans le cadre de la prise en charge de l'évaluateur d'expression les visualiseurs de type.  
  
## Remarques pour les appelants  
 Appelez [QueryInterface](/visual-cpp/atl/queryinterface) à une interface de `IDebugProperty3` pour obtenir cette interface.  
  
## méthodes en commande de Vtable  
 L'interface d' `IPropertyProxyProvider` implémente la méthode suivante :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Extrait une interface de proxy de propriété pour afficher des données sur un objet.|  
  
## Notes  
 Bien que l'évaluateur d'expression implémente cette interface, l'implémentation de [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) est généralement gérée par [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md).  Consultez [Visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md) pour plus d'informations sur l'obtention de l'interface d'IEEVisualizerService.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [Visualiseur de type et de la visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [Visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md)