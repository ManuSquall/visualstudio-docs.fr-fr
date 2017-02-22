---
title: "IDebugPortEx2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEx2"
helpviewer_keywords: 
  - "Interface de IDebugPortEx2"
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugPortEx2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface permet au gestionnaire de débogage de session \(SDM\) contrôler les programmes et processus qui s'exécutent sur un port.  
  
## Syntaxe  
  
```  
IDebugPortEx2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Un fournisseur de port implémente cette interface sur le même objet qui implémente [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md).  
  
## Remarques pour les appelants  
 Le SDM appelle [QueryInterface](/visual-cpp/atl/queryinterface) sur l'interface d' `IDebugPort2` pour obtenir cette interface.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugPortEx2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|lance un fichier exécutable.|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Reprend l'exécution d'un processus.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|détermine si un processus peut être terminé.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Terminer un processus.|  
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|obtient l'ID de processus du port lui\-même.|  
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Obtient un programme associé à un nœud de programme.|  
  
## Notes  
 Cette interface est normalement privée entre le SDM et le fournisseur de port.  
  
 Si vous le souhaitez, un \(DE\) moteur de débogage peut rechercher cette interface sur l'interface d' [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) passée à [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) et utiliser [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) pour exécuter le programme.  Ce n'est pas obligatoire ; toutefois, et un De peut faire tout ce qu'il doit effectuer pour exécuter le programme de requête.  
  
## Configuration requise  
 en\-tête : portpriv.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)