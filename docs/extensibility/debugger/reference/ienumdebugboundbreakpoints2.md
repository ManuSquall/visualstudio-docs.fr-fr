---
title: "IEnumDebugBoundBreakpoints2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugBoundBreakpoints2"
helpviewer_keywords: 
  - "IEnumDebugBoundBreakpoints2"
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEnumDebugBoundBreakpoints2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface énumère les points d'arrêt liés associés à un point d'arrêt en attente ou un événement lié de point d'arrêt.  
  
## Syntaxe  
  
```  
IEnumDebugBoundBreakpoints2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le moteur de \(DE\) débogage implémente cette interface dans le cadre de son prise en charge des points d'arrêt.  Cette interface doit être implémentée si les points d'arrêt sont pris en charge.  
  
## Remarques pour les appelants  
 appels de Visual Studio :  
  
-   [EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) pour obtenir cette interface représentant une liste de tous les points d'arrêt qui sont déclenchés.  
  
-   [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) pour obtenir cette interface représentant une liste de tous les points d'arrêt qui ont été liés.  
  
-   [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) pour obtenir cette interface représentant une liste de tous les points d'arrêt les lie à ce point d'arrêt en attente.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IEnumDebugBoundBreakpoints2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[Suivant](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|Récupère un nombre spécifié de points d'arrêt liés dans une séquence d'énumération.|  
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|Ignore un nombre spécifié de points d'arrêt liés dans une séquence d'énumération.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|réinitialise une séquence d'énumération au début.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|crée un énumérateur qui contient le même état d'énumération que l'énumérateur actuel.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|obtient le nombre de points d'arrêt liés dans un énumérateur.|  
  
## Notes  
 Visual Studio utilise des points d'arrêt liés représentés par cette interface pour mettre à jour l'affichage des points d'arrêt dans l'IDE.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)