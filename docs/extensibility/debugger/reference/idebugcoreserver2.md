---
title: "IDebugCoreServer2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer2"
helpviewer_keywords: 
  - "Interface de IDebugCoreServer2"
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugCoreServer2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface est utilisée pour représenter et obtenir des informations à partir d'un serveur sur un ordinateur sur le réseau.  
  
## Syntaxe  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Visual Studio implémente cette interface pour représenter un serveur.  chaque instance de Visual Studio crée une instance de cette interface.  
  
## Remarques pour les appelants  
 Un fournisseur de port reçoit cette interface dans un appel à [Événement](../../../extensibility/debugger/reference/idebugportevents2-event.md).  
  
 Un moteur de débogage peut obtenir cette interface indirectement via un appel à [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) \(qui retourne [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md), une interface dérivée d' `IDebugCoreServer2`\).  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugCoreServer2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetMachineInfo](../Topic/IDebugCoreServer2::GetMachineInfo.md)|obtient le nom et les attributs d'un ordinateur.|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|obtient le nom d'un ordinateur.|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|obtient un fournisseur de port qui existe sur un ordinateur.|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|obtient un port qui existe déjà sur un ordinateur.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|crée un énumérateur pour tous les ports sur un ordinateur.|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|crée un énumérateur pour tous les fournisseurs de port sur un ordinateur.|  
|[GetMachineUtilities\_V7](../Topic/IDebugCoreServer2::GetMachineUtilities_V7.md)|obtient les utilitaires d'ordinateur pour un ordinateur.|  
  
## Notes  
 Cette interface est également utilisée par Visual Studio pour parcourir des processus qui s'exécutent sur des ordinateurs du réseau.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [Événement](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)