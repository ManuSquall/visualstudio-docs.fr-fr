---
title: "IEnumDebugAddresses | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugAddresses"
helpviewer_keywords: 
  - "Interface de IEnumDebugAddresses"
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IEnumDebugAddresses
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette interface représente une collection d'objets implémentant l'interface d' [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
## Syntaxe  
  
```  
IEnumDebugAdresses : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 cette interface est implémentée par le fournisseur de symbole pour fournir des ensembles d'objets qui implémentent l'interface d' [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  Notez que ce n'est pas une énumération standard COM en raison de la présence de la méthode d' [GetCount](../Topic/IEnumDebugAddresses::GetCount.md) .  
  
## Remarques pour les appelants  
 cette interface est retournée par [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) et [GetAddressesFromPosition](../Topic/IDebugSymbolProvider::GetAddressesFromPosition.md).  
  
## méthodes en commande de Vtable  
 Cette interface implémente les méthodes suivantes.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Suivant](../Topic/IEnumDebugAddresses::Next.md)|extrait l'ensemble suivant d'objets d' [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) de l'énumération.|  
|[Ignorer](../Topic/IEnumDebugAddresses::Skip.md)|Ignore un nombre spécifié d'entrées.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|réinitialise l'énumération à la première entrée.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|extrait une copie de l'énumération actuelle.|  
|[GetCount](../Topic/IEnumDebugAddresses::GetCount.md)|Récupère le nombre d'entrées de l'énumération.|  
  
## Notes  
 Cette interface est généralement utilisée par le moteur de débogage pour déterminer l'adresse appropriée pour donner à l'évaluateur d'expression.  
  
## Configuration requise  
 en\-tête : sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [GetAddressesFromPosition](../Topic/IDebugSymbolProvider::GetAddressesFromPosition.md)