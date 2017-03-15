---
title: "Visualisation et affichage des donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "débogage (débogage SDK), l'affichage des données"
  - "débogage (débogage SDK), la visualisation des données"
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Visualisation et affichage des donn&#233;es
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Tapez les données actuelles de visualiseurs et de visionneuses personnalisés d'une manière qui soit rapidement explicite à un développeur.  L'évaluateur \(EE\) d'expression peut prendre en charge des tiers visualiseurs de type ainsi que fournir ses propres visionneuses personnalisées.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] détermine le nombre de visualiseurs de type et de visionneuses personnalisées sont associées au type d'objet en appelant la méthode d' [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md) .  S'il y a au moins une visualiseur de type ou visionneuse de personnalisé disponible, Visual Studio appelle la méthode d' [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) pour récupérer une liste de ces visualiseurs et visionneuses \(en réalité, une liste d' `CLSID`des objets qui implémentent les visualiseurs et les visionneuses\) et les présente à l'utilisateur.  
  
## visualiseurs de prise en charge de type  
 Il existe un nombre quelconque d'interfaces que l'évaluateur d'expression doit implémenter pour prendre en charge les visualiseurs de type.  Ces interfaces peuvent être décomposées en deux grandes catégories : ceux qui répertorient les visualiseurs de type et ceux qui accèdent aux données de propriété.  
  
### répertorier des visualiseurs de type  
 L'évaluateur d'expression prend en charge répertorier les visualiseurs de type dans son implémentation d' `IDebugProperty3::GetCustomViewerCount` et d' `IDebugProperty3::GetCustomViewerList`.  ces méthodes passent l'appel aux méthodes correspondantes [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) et [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).  
  
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) est obtenu en appelant [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md).  Cette méthode requiert l'interface d' [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) , obtenue à partir de l'interface d' [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) passée à [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).  `IEEVisualizerServiceProvider::CreateVisualizerService` requiert également les interfaces d' [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) et d' [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) passées à `IDebugParsedExpression::EvaluateSync`.  L'interface finale requise pour créer l'interface d' `IEEVisualizerService` est l'interface d' [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) , que l'évaluateur d'expression implémente.  Cette interface autorise les modifications à effectuer à la propriété qui est visualisée.  Toutes les données de propriété est encapsulée dans une interface d' [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) , qui est également implémentée par l'évaluateur d'expression.  
  
### Accès aux données de propriété  
 L'accès aux données des propriétés s'effectue via l'interface d' [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) .  Pour obtenir cette interface, les appels [QueryInterface](/visual-cpp/atl/queryinterface) de Visual Studio à l'objet de propriété pour obtenir l'interface d' [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) \(implémentée sur le même objet qui implémente l'interface d' [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) \) et appelle ensuite la méthode d' [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) pour obtenir l'interface d' `IPropertyProxyEESide` .  
  
 Toutes les données passée dans ou hors de l'interface d' `IPropertyProxyEESide` est encapsulée dans l'interface d' [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) .  Cette interface représente un tableau d'octets et est implémentée par Visual Studio et l'évaluateur d'expression.  Lorsque les données d'une propriété doit être modifiée, Visual Studio crée un objet d' `IEEDataStorage` maintenant les nouvelles données et appelle [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) à cet objet de données pour obtenir un objet d' `IEEDataStorage` qui, à son tour, est passé à [InPlaceUpdateObject](../Topic/IPropertyProxyEESide::InPlaceUpdateObject.md) pour mettre à jour les données de la propriété.  `IPropertyProxyEESide::CreateReplacementObject` permet à l'évaluateur d'expression pour instancier sa propre classe qui implémente l'interface d' `IEEDataStorage` .  
  
## visionneuses personnalisées de prise en charge  
 La balise `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` est définie dans le domaine de `dwAttrib` de la structure de [DEBUG\_PROPERTY\_INFO](../../extensibility/debugger/reference/debug-property-info.md) \(retournée par un appel à [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)\) pour indiquer que l'objet a une visionneuse personnalisée qui lui est associée.  Lorsque cette balise est définie, Visual Studio obtient l'interface d' [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) de l'interface d' [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) à l'aide de [QueryInterface](/visual-cpp/atl/queryinterface).  
  
 Si l'utilisateur sélectionne une visionneuse personnalisée, Visual Studio instancie la visionneuse personnalisée à l'aide de `CLSID` de la visionneuse fourni par la méthode d' `IDebugProperty3::GetCustomViewerList` .  Visual Studio appelle ensuite [Valeur d'affichage](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) pour afficher la valeur à l'utilisateur.  
  
 Normalement, `IDebugCustomViewer::DisplayValue` présente une vue en lecture seule de données.  Pour autoriser des modifications apportées aux données, l'évaluateur d'expression doit implémenter une interface personnalisée qui prend en charge la modification des données sur un objet de propriété.  La méthode d' `IDebugCustomViewer::DisplayValue` utilise cette interface personnalisée pour prendre en charge la modification des données.  La méthode recherche l'interface personnalisée sur l'interface d' `IDebugProperty2` passée comme argument d' `pDebugProperty` .  
  
## Prendre en charge les visualiseurs de type et des visionneuses personnalisées  
 L'évaluateur d'expression peut prendre en charge les visualiseurs de type et des visionneuses personnalisées dans les méthodes d' [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md) et d' [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) .  Tout d'abord, l'évaluateur d'expression ajoute le nombre de visionneuses personnalisées qu'il fournit à la valeur retournée par la méthode d' [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) .  Ensuite, l'évaluateur d'expression ajoute `CLSID`s de ses propres visionneuses personnalisées à la liste retournée par la méthode d' [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) .  
  
## Voir aussi  
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)   
 [Visualiseur de type et de la visionneuse personnalisée](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)