---
title: "IEEDataStorage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEDataStorage"
helpviewer_keywords: 
  - "Interface de IEEDataStorage"
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEEDataStorage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface représente un tableau d'octets.  
  
## Syntaxe  
  
```  
IEEDataStorage : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 L'évaluateur \(EE\) d'expression implémente cette interface pour représenter un tableau d'octets \(utilisés par les visualiseurs de type pour récupérer et modifier les données via l'interface d' [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) \).  L'évaluateur d'expression implémente généralement cette interface pour prendre en charge les visualiseurs externes de type.  
  
## Remarques pour les appelants  
 Les méthodes sur `IPropertyProxyEESide` interface retourner la valeur cette interface.  appel [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) pour obtenir l'interface d' [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) .  Appelez [QueryInterface](/visual-cpp/atl/queryinterface) à une interface de [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) pour obtenir l'interface d' [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) .  
  
## méthodes en commande de Vtable  
 L'interface d' `IEEDataStorage` implémente les méthodes suivantes :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetData](../Topic/IEEDataStorage::GetData.md)|Récupère le nombre spécifié d'octets de données vers une mémoire tampon fournie.|  
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|Récupère le nombre d'octets de données disponibles.|  
  
## Notes  
 Cette interface est utilisée par un visualiseur de type pour accéder aux données gérées par un objet spécifique.  Les données sont traitées comme un tableau d'octets, permettant au visualiseur de type à manipuler dans le mode est requise pour le présenter à l'utilisateur.  
  
 Une visionneuse personnalisée peut également utiliser cette interface, si vous le souhaitez, bien que plus classique, une visionneuse personnalisée utilise une interface personnalisée, [GetMemoryBytes](../Topic/IDebugProperty2::GetMemoryBytes.md) ou [GetStringChars](../Topic/IDebugProperty3::GetStringChars.md) \(pour les données chaîne\-orientées\).  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [Visualiseur de type et de la visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)