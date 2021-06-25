---
title: Méthodes Breakpoint-Related | Microsoft Docs
description: Le débogage Visual Studio prend en charge les points d’arrêt liés, qui sont liés avec succès à un emplacement dans le code, et les points d’arrêt en attente, qui ne sont pas encore liés.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ec218cea05dffc1c558cabdef47895da9ad7ba9c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901498"
---
# <a name="breakpoint-related-methods"></a>Méthodes liées aux points d’arrêt
Un moteur de débogage (DE) doit prendre en charge le paramètre des points d’arrêt. Le débogage Visual Studio prend en charge les types de points d’arrêt suivants :

- Limite

     Demandé par le biais de l’interface utilisateur et correctement lié à un emplacement de code spécifié

- Pending

     Demandé par le biais de l’interface utilisateur mais pas encore lié à des instructions réelles

## <a name="discussion"></a>Discussion
 Par exemple, un point d’arrêt en attente se produit lorsque les instructions ne sont pas encore chargées. Lorsque le code est chargé, les points d’arrêt en attente essaient de se lier au code à l’emplacement prescrit, c’est-à-dire d’insérer des instructions d’arrêt dans le code. Les événements sont envoyés au gestionnaire de débogage de session (SDM) pour indiquer la réussite de la liaison ou signaler des erreurs de liaison.

 Un point d’arrêt en attente gère également sa propre liste interne de points d’arrêt liés correspondants. Un point d’arrêt en attente peut entraîner l’insertion de nombreux points d’arrêt dans le code. L’interface utilisateur de débogage de Visual Studio affiche une arborescence des points d’arrêt en attente et leurs points d’arrêt liés correspondants.

 La création et l’utilisation de points d’arrêt en attente requièrent l’implémentation de la méthode [IDebugEngine2 :: CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) , ainsi que les méthodes suivantes des interfaces [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) .

|Méthode|Description|
|------------|-----------------|
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Détermine si un point d’arrêt en attente spécifié peut être lié à un emplacement de code.|
|[Établis](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Lie un point d’arrêt en attente spécifié à un ou plusieurs emplacements de code.|
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Obtient l’état d’un point d’arrêt en attente.|
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Obtient la demande de point d’arrêt utilisée pour créer un point d’arrêt en attente.|
|[Activer](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Active/désactive l’état activé d’un point d’arrêt en attente.|
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Énumère tous les points d’arrêt liés à partir d’un point d’arrêt en attente.|
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Énumère tous les points d’arrêt d’erreur qui résultent d’un point d’arrêt en attente.|
|[Supprimer](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Supprime un point d’arrêt en attente et tous les points d’arrêt liés à celui-ci.|

 Pour énumérer les points d’arrêt liés et les points d’arrêt d’erreur, vous devez implémenter toutes les méthodes de [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) et de [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).

 Les points d’arrêt en attente qui lient à un emplacement de code requièrent l’implémentation des méthodes [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) suivantes.

|Méthode|Description|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Obtient le point d’arrêt en attente qui contient un point d’arrêt.|
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Obtient l’état d’un point d’arrêt lié.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Obtient la résolution de point d’arrêt qui décrit un point d’arrêt.|
|[Activer](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Active ou désactive un point d’arrêt.|
|[Supprimer](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Supprime un point d’arrêt lié.|

 Les informations de résolution et de demande requièrent l’implémentation des méthodes [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) suivantes.

|Méthode|Description|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Obtient le type du point d’arrêt représenté par une résolution.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Obtient les informations de résolution de point d’arrêt qui décrivent un point d’arrêt.|

 La résolution des erreurs qui peuvent se produire pendant la liaison nécessite l’implémentation des méthodes [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) suivantes.

|Méthode|Description|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Obtient le point d’arrêt en attente qui contient un point d’arrêt d’erreur.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Obtient la résolution d’erreur de point d’arrêt qui décrit un point d’arrêt d’erreur.|

 La résolution des erreurs qui peuvent se produire pendant la liaison requiert également les méthodes suivantes de [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).

|Méthode|Description|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Obtient le type d’un point d’arrêt.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Obtient les informations de résolution d’un point d’arrêt.|

 Pour afficher le code source à un point d’arrêt, vous devez implémenter les méthodes de [IDebugStackFrame2 :: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) et/ou les méthodes de [IDebugStackFrame2 :: GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).

## <a name="see-also"></a>Voir aussi
- [Contrôle d’exécution et évaluation de l’État](../../extensibility/debugger/execution-control-and-state-evaluation.md)
