---
title: "IDebugPortSupplier3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier3"
helpviewer_keywords: 
  - "Interface de IDebugPortSupplier3"
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPortSupplier3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface permet à un appelant pour déterminer si un fournisseur de port peut conserver des ports \(en les entrant sur le disque\) entre les appels du débogueur puis accéder à une liste de celles les ports conservés.  
  
## Syntaxe  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## Remarques à l'intention des implémenteurs  
 Un fournisseur de port implémente cette interface pour prendre en charge la persistance ou enregistrer des informations sur le port sur le disque.  cette interface doit être implémentée sur le même objet que l'interface d' [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) .  
  
## Remarques pour les appelants  
 Appelez [QueryInterface](/visual-cpp/atl/queryinterface) à l'interface d' `IDebugPortSupplier2` pour obtenir cette interface.  
  
## méthodes en commande de Vtable  
 En plus de les méthodes héritées de l'interface d' [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) , cette interface prend en charge les éléments suivants :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Retourne la valeur si le fournisseur de port peut conserver des ports \(en les entrant sur le disque\) entre les appels du débogueur.|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Retourne un objet qui peut être utilisé pour l'énumérer tous les ports qui ont été écrites sur le disque par ce fournisseur de port.|  
  
## Notes  
 Si un fournisseur de port peut conserver des ports à travers les appels, il doit implémenter cette interface.  Les ports doivent être chargés lorsque le fournisseur de port est instancié, et écrit sur le disque lorsque le fournisseur de port est détruit.  
  
 Un moteur de débogage en général n'interagissent pas avec un fournisseur de port et ne présente aucune utilisation de l'interface.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)