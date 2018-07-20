---
title: Méthodes de point d’arrêt | Microsoft Docs
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
ms.openlocfilehash: e7e823c5fef66077ba03d4cb9eec4367b79038db
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152141"
---
# <a name="breakpoint-related-methods"></a>Méthodes de point d’arrêt
Un moteur de débogage (dé) doit prendre en charge le paramètre de points d’arrêt. Débogage de Visual Studio prend en charge les types de points d’arrêt suivants :  
  
-   lié  
  
     Demandés via l’interface utilisateur et correctement lié à un emplacement de code spécifié  
  
-   En attente  
  
     Demandé par l’interface utilisateur, mais pas encore lié aux véritables instructions  
  
## <a name="discussion"></a>Discussion  
 Par exemple, un point d’arrêt en attente se produit lorsque les instructions ne sont pas encore chargées. Lorsque le code est chargé, en attente de points d’arrêt try à lier au code à l’emplacement indiqué, autrement dit, pour insérer des instructions de saut dans le code. Événements sont envoyés vers le Gestionnaire de session de débogage (SDM) pour indiquer la liaison réussie ou pour avertir qu’il existait des erreurs de liaison.  
  
 Un point d’arrêt en attente gère également sa propre liste interne des points d’arrêt liés correspondants. Une attente de point d’arrêt peut provoquer l’insertion de nombreux points d’arrêt dans le code. Débogage de l’interface utilisateur de Visual Studio affiche une arborescence de commandes de l’attente des points d’arrêt et leurs correspondantes des points d’arrêt liés.  
  
 Création et l’utilisation de points d’arrêt dans l’attente nécessitent l’implémentation de la [IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) (méthode), ainsi que les méthodes suivantes de [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfaces.  
  
|Méthode|Description|  
|------------|-----------------|  
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Détermine si un texte spécifié en attente de point d’arrêt peut lier à un emplacement de code.|  
|[Lier](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Lie un spécifié en attente de point d’arrêt à un ou plusieurs emplacements de code.|  
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Obtient l’état d’un point d’arrêt en attente.|  
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Obtient la point d’arrêt de demande utilisé pour créer un point d’arrêt en attente.|  
|[Activer](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Active ou désactive l’état activé d’un point d’arrêt en attente.|  
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Énumère tous les points d’arrêt liés à partir d’un point d’arrêt en attente.|  
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Énumère toutes les erreurs des points d’arrêt qui résultent d’un point d’arrêt en attente.|  
|[Supprimer](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Supprime un point d’arrêt en attente et tous les points d’arrêt liés à partir de celui-ci.|  
  
 Pour énumérer les points d’arrêt liés et les points d’arrêt de l’erreur, vous devez implémenter toutes les méthodes de [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) et de [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).  
  
 En attente de points d’arrêt lier à un code emplacement nécessitent l’implémentation des opérations suivantes [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) méthodes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Obtient le point d’arrêt en attente qui contient un point d’arrêt.|  
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Obtient l’état d’un point d’arrêt lié.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Obtient la résolution de point d’arrêt qui décrit un point d’arrêt.|  
|[Activer](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Active ou désactive un point d’arrêt.|  
|[Supprimer](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Supprime un point d’arrêt lié.|  
  
 Demande d’informations nécessitent l’implémentation des éléments suivants et la résolution [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) méthodes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Obtient le type du point d’arrêt représenté par une résolution.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Obtient les informations de résolution de point d’arrêt qui décrit un point d’arrêt.|  
  
 Résolution des erreurs qui peuvent se produire lors de la liaison nécessite l’implémentation des opérations suivantes [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) méthodes.  
  
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
 [Évaluation de contrôle et l’état d’exécution](../../extensibility/debugger/execution-control-and-state-evaluation.md)