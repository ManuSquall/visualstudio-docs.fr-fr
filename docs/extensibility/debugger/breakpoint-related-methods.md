---
title: Méthodes de point d’arrêt | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce44a7d3d3578d5157bcefcf14172d92ece677d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107288"
---
# <a name="breakpoint-related-methods"></a>Méthodes de point d’arrêt
Un moteur de débogage (DE) doit prendre en charge la définition de points d’arrêt. Débogage de Visual Studio prend en charge les types de points d’arrêt suivants :  
  
-   Lié  
  
     Demandés via l’interface utilisateur et correctement lié à un emplacement de code spécifié  
  
-   En attente  
  
     Demandés via l’interface utilisateur, mais pas encore lié à réelle des instructions  
  
## <a name="discussion"></a>Discussion  
 Par exemple, un point d’arrêt en attente se produit lorsque les instructions ne sont pas encore chargées. Lorsque le code est chargé, en attente de points d’arrêt try à lier au code à l’emplacement prescrite, autrement dit, pour insérer des instructions de saut dans le code. Les événements sont envoyés vers le Gestionnaire de session de débogage (SDM) pour indiquer la liaison réussie ou pour avertir qu’il existait des erreurs de liaison.  
  
 Un point d’arrêt en attente gère également sa propre liste interne des points d’arrêt lié correspondant. Une attente de point d’arrêt peut provoquer l’insertion d’un grand nombre de points d’arrêt dans le code. Le débogage de l’interface utilisateur Visual Studio affiche une arborescence de commandes d’en attente de points d’arrêt et leurs correspondantes des points d’arrêt liés.  
  
 Création et l’utilisation de points d’arrêt dans l’attente requièrent l’implémentation de la [IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) (méthode), ainsi que les méthodes suivantes de [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfaces.  
  
|Méthode|Description|  
|------------|-----------------|  
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Détermine si un élément spécifié en attente de point d’arrêt peut lier à un emplacement du code.|  
|[Lier](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Lie un spécifié en attente de point d’arrêt à un ou plusieurs emplacements de code.|  
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Obtient l’état d’un point d’arrêt en attente.|  
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Obtient la demande de point d’arrêt permet de créer un point d’arrêt en attente.|  
|[Activer](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Active ou désactive l’état activé d’un point d’arrêt en attente.|  
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Énumère tous les points d’arrêt liés à partir d’un point d’arrêt en attente.|  
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Énumère tous les points d’arrêt erreur résultant d’un point d’arrêt en attente.|  
|[Supprimer](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Supprime un point d’arrêt en attente et tous les points d’arrêt liés à partir de celui-ci.|  
  
 Pour énumérer les points d’arrêt liés et les points d’arrêt de l’erreur, vous devez implémenter toutes les méthodes de [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) et de [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).  
  
 En attente de points d’arrêt à lier à un code d’emplacement nécessite l’implémentation des opérations suivantes [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) méthodes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Obtient le point d’arrêt en attente qui contient un point d’arrêt.|  
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Obtient l’état d’un point d’arrêt lié.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Obtient la résolution de point d’arrêt qui décrit un point d’arrêt.|  
|[Activer](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Active ou désactive un point d’arrêt.|  
|[Supprimer](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Supprime un point d’arrêt lié.|  
  
 Demande d’informations requièrent une implémentation de la commande suivante et la résolution [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) méthodes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Obtient le type du point d’arrêt représenté par une résolution.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Obtient les informations de résolution de point d’arrêt qui décrit un point d’arrêt.|  
  
 Résolution des erreurs qui peuvent se produire lors de la liaison nécessite l’implémentation de ces [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) méthodes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Obtient le point d’arrêt en attente qui contient un point d’arrêt de l’erreur.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Obtient la résolution d’erreur de point d’arrêt qui décrit un point d’arrêt de l’erreur.|  
  
 Résolution des erreurs qui peuvent se produire lors de la liaison requiert également les méthodes suivantes de [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Obtient le type d’un point d’arrêt.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Obtient les informations de résolution d’un point d’arrêt.|  
  
 Affichage du code source à un point d’arrêt vous oblige à implémenter les méthodes de [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) et/ou les méthodes de [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôle de l’exécution et évaluation de l’état](../../extensibility/debugger/execution-control-and-state-evaluation.md)