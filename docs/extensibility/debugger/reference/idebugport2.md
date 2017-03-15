---
title: "IDebugPort2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPort2"
helpviewer_keywords: 
  - "Interface de IDebugPort2"
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugPort2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette interface représente un port de débogage sur un ordinateur.  
  
## Syntaxe  
  
```  
IDebugPort2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Un fournisseur de port implémente cette interface pour représenter un port de débogage sur un ordinateur.  
  
 Si le port prend en charge les événements de port d'émission, il doit également implémenter l'interface d' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> pour prendre en charge une interface d' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> qui fournit ensuite l'interface d' [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) .  
  
## Remarques pour les appelants  
 Appels au retour d' [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) ou d' [Ajouter un port](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) cette interface, qui représente le port demandé.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugPort2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Retourne le nom de port.|  
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Retourne l'identificateur de port.|  
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Retourne la requête utilisée pour créer un port \(si disponible\).|  
|[GetPortSupplier](../Topic/IDebugPort2::GetPortSupplier.md)|Retourne le fournisseur de port pour ce port.|  
|[GetProcess](../Topic/IDebugPort2::GetProcess.md)|Retourne une interface au processus donné l'identificateur du processus.|  
|[EnumProcesses](../Topic/IDebugPort2::EnumProcesses.md)|Énumère tous les processus qui s'exécutent sur un port.|  
  
## Notes  
 Le port local permet d'accéder à tous les processus et programme à s'exécuter sur l'ordinateur local.  D'autres ports peut représenter une jonction de câble série à un appareil Windows CE, ou une connexion réseau à un ordinateur de non\-DCOM.  L'interface d' `IDebugPort2` est utilisée pour rechercher le nom et l'ID d'un port, énumérer tous processus qui s'exécutent sur le port, et fournit des fonctionnalités pour démarrer et arrêter des processus sur le port.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)