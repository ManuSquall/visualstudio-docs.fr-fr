---
title: "IDebugPendingBreakpoint2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPendingBreakpoint2"
helpviewer_keywords: 
  - "Interface de IDebugPendingBreakpoint2"
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugPendingBreakpoint2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface représente un point d'arrêt qui est prêt à le lier à un emplacement du code.  
  
## Syntaxe  
  
```  
IDebugPendingBreakpoint2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le moteur de \(DE\) débogage implémente cette interface dans le cadre de son prise en charge des points d'arrêt.  
  
## Remarques pour les appelants  
 un appel à [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) crée un point d'arrêt en attente d'une interface d' [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) .  un appel à [Lier](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) crée une interface d' `IDebugBreakpoint2` qui représente un point d'arrêt lié dans le programme.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugPendingBreakpoint2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Détermine si ce point d'arrêt en attente peut être lié à un emplacement du code.|  
|[Lier](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Lie ce point d'arrêt en attente à un ou plusieurs emplacements de code.|  
|[GetState](../Topic/IDebugPendingBreakpoint2::GetState.md)|Obtient l'état de ce point d'arrêt en attente.|  
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Obtient la requête de point d'arrêt qui a été utilisée pour créer ce point d'arrêt en attente.|  
|[Virtualiser](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Bascule l'état virtualisé de ce point d'arrêt en attente.|  
|[Activer](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Bascule l'état actif de ce point d'arrêt en attente.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Définit ou modifie la condition associée à ce point d'arrêt en attente.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Définit ou modification que le nombre de passage associé à ce point d'arrêt en attente.|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Énumère tous les points d'arrêt liés de ce point d'arrêt en attente.|  
|[EnumErrorBreakpoints](../Topic/IDebugPendingBreakpoint2::EnumErrorBreakpoints.md)|Énumère tous les points d'arrêt d'erreur qui ont résulté de ce point d'arrêt en attente.|  
|[Supprimer](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Supprime ce point d'arrêt en attente et tous les points d'arrêt liés de lui.|  
  
## Notes  
 `IDebugPendingBreakpoint2` peut être considéré comme un fournisseur de toutes les informations nécessaires nécessaire de lier un point d'arrêt au code qui peut être appliquée à un ou plusieurs programmes.  
  
 Un point d'arrêt en attente peut potentiellement produire plusieurs points d'arrêt lié.  Par exemple, un point d'arrêt dans le modèle C\/C\+\+ \+\+\-style peut produire un point d'arrêt liés pour chaque instance unique de ce modèle.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../Topic/IDebugBoundBreakpoint2::GetPendingBreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)