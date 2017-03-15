---
title: "IDebugProgramHost2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramHost2"
helpviewer_keywords: 
  - "Interface de IDebugProgramHost2"
ms.assetid: 2c37b3aa-97a9-4665-8709-edd917f18cb1
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgramHost2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface fournit des informations \(de processus\) d'hôte à propos d'un programme.  
  
## Syntaxe  
  
```  
IDebugProgramHost2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le moteur de débogage implémente cette interface sur le même objet que l'interface d' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) pour fournir des informations sur le processus d'hébergement.  Il s'agit d'une interface facultative.  
  
## Remarques pour les appelants  
 Appelez [QueryInterface](/visual-cpp/atl/queryinterface) à une interface de `IDebugProgram2` pour obtenir cette interface.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugProgramHost2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostname.md)|obtient le titre, le nom convivial, ou le nom de fichier du processus d'hébergement de ce programme.|  
|[GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)|Obtient l'identificateur du processus d'hébergement de ce programme.|  
|[GetHostMachineName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostmachinename.md)|Obtient le nom de l'ordinateur sur lequel le processus d'hébergement de ce programme s'exécute.|  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)