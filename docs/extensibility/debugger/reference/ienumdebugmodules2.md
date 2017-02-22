---
title: "IEnumDebugModules2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugModules2"
helpviewer_keywords: 
  - "IEnumDebugModules2"
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEnumDebugModules2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface énumère une liste des modules.  
  
## Syntaxe  
  
```  
IEnumDebugModules2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le moteur \(DE\) de débogage implémente cette interface pour représenter une liste des modules chargés pour un programme.  
  
## Remarques pour les appelants  
 Visual Studio appelle [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) pour obtenir cette interface.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IEnumDebugModules2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Suivant](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Récupère un nombre spécifié de modules dans une séquence d'énumération.|  
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Ignore un nombre spécifié de modules dans une séquence d'énumération.|  
|[Réinitialiser](../Topic/IEnumDebugModules2::Reset.md)|réinitialise une séquence d'énumération au début.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|crée un énumérateur qui contient le même état d'énumération que l'énumérateur actuel.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|obtient le nombre de modules.|  
  
## Notes  
 Visual Studio utilise cette interface principalement pour mettre à jour la fenêtre de **Module** .  
  
 Pour les besoins de débogage dans Visual Studio, un programme est une séquence logique d'instruction de code qui peut traverser des limites de module, d'où la nécessité de liste de modules pour une interface unique d' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) .  Le premier module dans la liste contient en général le point d'entrée initiale pour le programme associé.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)