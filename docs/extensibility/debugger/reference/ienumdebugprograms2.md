---
title: "IEnumDebugPrograms2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPrograms2"
helpviewer_keywords: 
  - "IEnumDebugPrograms2"
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEnumDebugPrograms2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface énumère les programmes s'exécutant dans une session de débogage en cours.  
  
## Syntaxe  
  
```  
IEnumDebugPrograms2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le moteur \(DE\) de débogage implémente cette interface pour fournir une liste des programmes débogué par le De.  
  
## Remarques pour les appelants  
 Visual Studio appelle [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) pour obtenir cette interface.  [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) n'est pas utilisé par Visual Studio.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IEnumDebugPrograms2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Suivant](../Topic/IEnumDebugPrograms2::Next.md)|Récupère un nombre spécifié de programmes dans une séquence d'énumération.|  
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Ignore un nombre spécifié de programmes dans une séquence d'énumération.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|réinitialise une séquence d'énumération au début.|  
|[Clone](../Topic/IEnumDebugPrograms2::Clone.md)|crée un énumérateur qui contient le même état d'énumération que l'énumérateur actuel.|  
|[GetCount](../Topic/IEnumDebugPrograms2::GetCount.md)|Obtient le nombre de programmes d'un énumérateur.|  
  
## Notes  
 Visual Studio utilise cette interface :  
  
-   Remplissez la fenêtre de **Module** \(en appelant [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) puis en appelant [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) sur chaque programme\).  
  
-   Remplissez liste d' **Attacher au processus** \(en appelant `IDebugProcess2::EnumPrograms` puis en appelant [QueryInterface](/visual-cpp/atl/queryinterface) sur chaque interface d' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) pour obtenir une interface d' [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) \).  
  
-   Générez une liste de les qui peut mettre chaque programme dans le processus \(à l'aide de [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)\).  
  
-   Appliquez la modification et continuez avec les mises à jour \(P.J.\) à chaque programme \(en appelant IDebugProcess2 : : [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)d'EnumPrograms puis de appeler\).  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)