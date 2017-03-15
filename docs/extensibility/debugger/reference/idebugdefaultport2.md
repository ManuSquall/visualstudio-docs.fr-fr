---
title: "IDebugDefaultPort2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDefaultPort2"
helpviewer_keywords: 
  - "Interface de IDebugDefaultPort2"
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDefaultPort2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface fournit plusieurs méthodes pour accéder aux fonctionnalités du serveur et de la notification d'un port.  
  
## Syntaxe  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## Remarques à l'intention des implémenteurs  
 Visual Studio implémente cette interface pour représenter le port de débogage pour les programmes d'accès.  Un fournisseur de port peut également implémenter cette interface s'il gère le débogage distant.  
  
## Remarques pour les appelants  
 un argument aux méthodes sur l'interface d' [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) fournit cette interface.  appeler [QueryInterface](/visual-cpp/atl/queryinterface) sur une interface d' [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) peut également obtenir cette interface.  
  
## méthodes en commande de Vtable  
 En plus de les méthodes définies dans [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetPortNotify](../Topic/IDebugDefaultPort2::GetPortNotify.md)|obtient l'interface de notification de port de ce port.|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Obtient l'interface au serveur qui héberge ce port.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Détermine si ce port s'exécute sur l'ordinateur local.|  
  
## Notes  
 Le nom « `IDebugDefaultPort2` » est un peu d'un terme mal approprié, car il ne représente pas un port par défaut.  Cela peut être nommé « IDebugPort3 ».  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)