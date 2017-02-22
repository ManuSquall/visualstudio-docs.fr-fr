---
title: "IDebugCoreServer3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer3"
helpviewer_keywords: 
  - "Interface de IDebugCoreServer3"
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCoreServer3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface fournit l'accès aux données sur le serveur que le processus s'exécute dans.  
  
## Syntaxe  
  
```  
IDebugCoreServer3 : IDebugCoreServer2  
```  
  
## Remarques à l'intention des implémenteurs  
 Visual Studio implémente cette interface.  
  
## Remarques pour les appelants  
 utilisation [QueryInterface](/visual-cpp/atl/queryinterface) d'obtenir cette interface d'une interface d' [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) .  Un appel à [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) peut également retourner cette interface.  Cette interface est la plus fréquemment utilisée par un fournisseur personnalisé de port pour exécuter les programmes sur un serveur \(soit local ou distant\).  
  
## méthodes en commande de Vtable  
 En plus de les méthodes sur l'interface d' [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) , cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|extrait le nom du serveur.|  
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|extrait une version conviviale du nom du serveur|  
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Indique les moteurs de débogage spécifiques de l'attachement automatiquement aux processus au début de ces processus.|  
|[DiagnoseWebDebuggingError](../Topic/IDebugCoreServer3::DiagnoseWebDebuggingError.md)|Récupère le code d'erreur spécifique lorsque l'attachement automatique échoue.|  
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|crée une instance d'un moteur de débogage sur le serveur.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|extrait une balise indiquant si le serveur est sur le même ordinateur que l'appelant.|  
|[GetConnectionProtocol](../Topic/IDebugCoreServer3::GetConnectionProtocol.md)|Récupère une valeur indiquant le protocole utilisé pour communiquer avec le serveur.|  
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Désactive tous les paramètres de l'auto\-attachement pour tous les moteurs de débogage que ce serveur connaît.|  
  
## Notes  
 Un fournisseur de port reçoit l'interface d' [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) sur un appel à [Événement](../../../extensibility/debugger/reference/idebugportevents2-event.md).  L'interface d' `IDebugCoreServer3` peut être obtenu à partir de cette interface.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)