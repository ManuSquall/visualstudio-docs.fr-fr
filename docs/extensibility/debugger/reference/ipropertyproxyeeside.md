---
title: "IPropertyProxyEESide | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IPropertyProxyEESide"
helpviewer_keywords: 
  - "Interface de IPropertyProxyEESide"
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IPropertyProxyEESide
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface fournit des méthodes pour afficher des données sur l'objet associé.  Cette interface fait partie de la prise en charge des visualiseurs de type.  
  
## Syntaxe  
  
```  
IPropertyProxyEESide : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Un évaluateur d'expression implémente cette interface pour prendre en charge les visualiseurs de type.  
  
## Remarques pour les appelants  
 appel [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) pour obtenir cette interface.  appelez [QueryInterface](/visual-cpp/atl/queryinterface) sur une interface d' [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) pour obtenir l'interface d' [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) .  
  
## méthodes en commande de Vtable  
 les méthodes suivantes sont implémentées par cette interface :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Initialise un fournisseur de sources de données afin que les données de l'objet pouvoir accéder.|  
|[GetManagedViewerCreationData](../Topic/IPropertyProxyEESide::GetManagedViewerCreationData.md)|Récupère des informations à propos de l'assembly de l'objet.|  
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|obtient les données initiales pour l'objet.|  
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|crée une copie d'un stockage des données existant.|  
|[InPlaceUpdateObject](../Topic/IPropertyProxyEESide::InPlaceUpdateObject.md)|crée une référence à un stockage des données existant.|  
|[ResolveAssemblyRef](../Topic/IPropertyProxyEESide::ResolveAssemblyRef.md)|Récupère des informations sur un assembly spécifique dans le contexte de l'assembly contenant cet objet.|  
  
## Notes  
 Un visualiseur de type utilise cette interface pour accéder aux valeurs associées à l'objet que cette interface fait partie de.  Les données via l'interface d' [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) , qui fournit une vue en lecture seule de données.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Visualiseur de type et de la visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)