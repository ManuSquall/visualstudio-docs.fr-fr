---
title: "IEnumDebugProcesses2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugProcesses2"
helpviewer_keywords: 
  - "IEnumDebugProcesses2"
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IEnumDebugProcesses2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface énumère les processus qui s'exécutent sur un port de débogage.  
  
## Syntaxe  
  
```  
IEnumDebugProcesses : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Un fournisseur de port implémente cette interface pour fournir une liste de processus qui s'exécutent sur un port.  
  
## Remarques pour les appelants  
 Visual Studio appelle [EnumProcesses](../Topic/IDebugPort2::EnumProcesses.md) pour obtenir cette interface.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IEnumDebugProcesses2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Suivant](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|Récupère un nombre spécifié de processus dans une séquence d'énumération.|  
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|Ignore un nombre spécifié de processus dans une séquence d'énumération.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|réinitialise une séquence d'énumération au début.|  
|[Clone](../Topic/IEnumDebugProcesses2::Clone.md)|crée un énumérateur qui contient le même état d'énumération que l'énumérateur actuel.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|obtient le nombre de processus dans un énumérateur.|  
  
## Notes  
 Visual Studio utilise cette interface pour remplir la fenêtre de **Processus** .  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumProcesses](../Topic/IDebugPort2::EnumProcesses.md)