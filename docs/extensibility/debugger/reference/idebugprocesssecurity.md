---
title: "IDebugProcessSecurity | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugProcessSecurity"
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugProcessSecurity
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

`IDebugProcessSecurity` est implémenté par un fournisseur de port pour avertir l'utilisateur que l'attachement au processus est potentiellement dangereux.  
  
## Syntaxe  
  
```  
IDebugProcessSecurity : IUnknown  
```  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugProcessSecurity`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|obtient le nom d'utilisateur du fournisseur de port.|  
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Avertit un utilisateur que l'attachement au processus de débogage n'est pas sécurisé.|  
  
## Notes  
 Implémentez cette interface pour afficher un avertissement et permettre à l'utilisateur d'annuler si le processus auquel vous joignez peut être considéré comme non sécurisé.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Ports](../../../extensibility/debugger/ports.md)   
 [Fournisseurs de port](../../../extensibility/debugger/port-suppliers.md)   
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)