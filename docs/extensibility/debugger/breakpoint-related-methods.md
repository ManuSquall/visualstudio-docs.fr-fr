---
title: "M&#233;thodes de point d&#39;arr&#234;t | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "méthodes de point d'arrêt de débogage [Debugging SDK],"
  - "points d'arrêt, méthodes"
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# M&#233;thodes de point d&#39;arr&#234;t
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un moteur de \(DE\) débogage doit prendre en charge les paramètres des points d'arrêt.  Prises en charge du débogage Visual Studio les types suivants de points d'arrêt :  
  
-   Dépendant  
  
     Demandé via l'interface utilisateur et avec succès lié à un emplacement spécifié de code  
  
-   En attente  
  
     Demandé via l'interface utilisateur mais pas encore lié aux instructions effectives  
  
## Discussion  
 Par exemple, un point d'arrêt en attente se produit lorsque l'instruction n'est pas encore chargée.  Lorsque le code est chargé, attendant essayez de points d'arrêt à le lier au code à l'emplacement recommandé, c. autrement dit., à l'instruction de saut d'insertion dans le code.  Les événements sont envoyés au gestionnaire de débogage de session \(SDM\) pour indiquer la liaison a réussi ou pour l'annoncer qu'il existait des erreurs de liaison.  
  
 un point d'arrêt en attente gère également sa propre liste interne de correspondre des points d'arrêt liés.  Un archivage en attente le point d'arrêt peut provoquer l'insertion de nombreux points d'arrêt dans le code.  Visual Studio le débogage de l'interface utilisateur affiche une arborescence des points d'arrêt en attente et de leurs points d'arrêt liés correspondants.  
  
 La création et l'utilisation des points d'arrêt en attente requièrent l'implémentation de la méthode d' [IDebugEngine2 : : CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) ainsi que des méthodes suivantes d'interfaces d' [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) .  
  
|Méthode|Description|  
|-------------|-----------------|  
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Détermine si un spécifié en attente le point d'arrêt peut être lié à un emplacement du code.|  
|[Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Lie un spécifié en attente le point d'arrêt à un ou plusieurs emplacements de code.|  
|[GetState](../Topic/IDebugPendingBreakpoint2::GetState.md)|Obtient l'état d'un point d'arrêt en attente.|  
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Obtient la requête de point d'arrêt utilisée pour créer un point d'arrêt en attente.|  
|[Activer](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|bascule l'état actif d'un point d'arrêt en attente.|  
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|énumère tous les points d'arrêt liés d'un point d'arrêt en attente.|  
|[EnumErrorBreakpoints](../Topic/IDebugPendingBreakpoint2::EnumErrorBreakpoints.md)|énumère tous les points d'arrêt d'erreur qui résultent d'un point d'arrêt en attente.|  
|[Supprimer](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|supprime un point d'arrêt en attente et tous points d'arrêt liés de lui.|  
  
 Pour énumérer les points d'arrêt liés et des points d'arrêt d'erreur, vous devez implémenter toutes les méthodes d' [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) et d' [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).  
  
 En attente les points d'arrêt qui les lient à un emplacement de code requièrent l'implémentation des méthodes suivantes pour [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) .  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetPendingBreakpoint](../Topic/IDebugBoundBreakpoint2::GetPendingBreakpoint.md)|obtient le point d'arrêt en attente qui contient un point d'arrêt.|  
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Obtient l'état d'un point d'arrêt lié.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|obtient la résolution de point d'arrêt qui décrit un point d'arrêt.|  
|[Activer](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|active ou désactive un point d'arrêt.|  
|[Supprimer](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|supprime un point d'arrêt lié.|  
  
 Les informations de résolution et de demande requièrent l'implémentation des méthodes suivantes pour [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) .  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|obtient le type du point d'arrêt représenté par une résolution.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|obtient les informations sur la résolution de point d'arrêt qui décrivent un point d'arrêt.|  
  
 La résolution des erreurs qui peuvent se produire pendant la liaison requiert l'implémentation des méthodes suivantes pour [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) .  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|obtient le point d'arrêt en attente qui contient un point d'arrêt d'erreur.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|obtient la résolution d'erreur de point d'arrêt qui décrit un point d'arrêt d'erreur.|  
  
 La résolution des erreurs qui peuvent se produire pendant la liaison requiert également les méthodes suivantes pour [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|obtient le type d'un point d'arrêt.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|obtient les informations sur la résolution d'un point d'arrêt.|  
  
 En affichant le code source à un point d'arrêt vous obligent à implémenter les méthodes d' [IDebugStackFrame2 : : GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) et\/ou les méthodes d' [IDebugStackFrame2 : : GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md).  
  
## Voir aussi  
 [Contrôle de l'exécution et l'évaluation de l'état](../../extensibility/debugger/execution-control-and-state-evaluation.md)