---
title: Méthodes liées aux points d’arrêt (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72ec63e500ac86a4a5bd66a2956fe0fb06c8834
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739211"
---
# <a name="breakpoint-related-methods"></a>Méthodes liées au point de rupture
Un moteur de débogé (DE) doit supporter le réglage des points de rupture. Le débogage Visual Studio prend en charge les types suivants de points d’arrêt :

- Limite

     Demandé par l’interface utilisateur et lié avec succès à un emplacement de code spécifié

- Pending

     Demandé par l’interface utilisateur mais pas encore lié aux instructions réelles

## <a name="discussion"></a>Discussions
 Par exemple, un point d’arrêt en attente se produit lorsque les instructions ne sont pas encore chargées. Lorsque le code est chargé, les points d’arrêt en attente tentent de se lier au code à l’emplacement prescrit, c’est-à-dire d’insérer des instructions de rupture dans le code. Les événements sont envoyés au gestionnaire de déboque de session (SDM) pour indiquer la liaison réussie ou pour aviser qu’il y avait des erreurs de liaison.

 Un point d’arrêt en attente gère également sa propre liste interne de points d’arrêt consolidés correspondants. Un point d’arrêt en attente peut provoquer l’insertion de nombreux points d’arrêt dans le code. L’interface utilisateur de débogage Visual Studio montre une vue d’arbre des points d’arrêt en attente et de leurs points de rupture liés correspondants.

 La création et l’utilisation des points d’arrêt en attente nécessitent la mise en œuvre de la méthode [IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) ainsi que les méthodes suivantes des interfaces [IDebugPendingBreakpoint2.](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)

|Méthode|Description|
|------------|-----------------|
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Détermine si un point d’arrêt en attente spécifié peut se lier à un emplacement de code.|
|[Lier](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Lie un point d’arrêt spécifié en attente à un ou plusieurs emplacements de code.|
|[GetState (en)](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Obtient l’état d’un point d’arrêt en attente.|
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Obtient la demande de point d’arrêt utilisé pour créer un point d’arrêt en attente.|
|[Activer](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Bascule l’état activé d’un point d’arrêt en attente.|
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Énumère tous les points d’arrêt liés à partir d’un point d’arrêt en attente.|
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Énumère tous les points d’erreur qui résultent d’un point d’arrêt en attente.|
|[Supprimer](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Supprime un point d’arrêt en attente et tous les points d’arrêt liés à partir de celui-ci.|

 Pour énumérer les points de rupture liés et les points d’erreur, vous devez mettre en œuvre toutes les méthodes [d’IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) et de [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).

 Les points d’arrêt en attente qui se lient à un emplacement de code nécessitent la mise en œuvre des méthodes [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) suivantes.

|Méthode|Description|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Obtient le point d’arrêt en attente qui contient un point d’arrêt.|
|[GetState (en)](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Obtient l’état d’un point d’arrêt lié.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Obtient la résolution de point d’arrêt qui décrit un point d’arrêt.|
|[Activer](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Permet ou désactive un point d’arrêt.|
|[Supprimer](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Supprime un point d’arrêt lié.|

 Les informations de résolution et de demande nécessitent la mise en œuvre des méthodes [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) suivantes.

|Méthode|Description|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Obtient le type de point d’arrêt représenté par une résolution.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Obtient les informations de résolution de point d’arrêt qui décrit un point d’arrêt.|

 La résolution des erreurs qui pourraient se produire pendant la liaison nécessite la mise en œuvre des méthodes [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) suivantes.

|Méthode|Description|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Obtient le point d’arrêt en attente qui contient un point d’erreur.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Obtient la résolution d’erreur de point de rupture qui décrit un point d’erreur.|

 La résolution des erreurs qui pourraient se produire lors de la liaison nécessite également les méthodes suivantes de [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).

|Méthode|Description|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Obtient le type de point d’arrêt.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Obtient les informations de résolution d’un point d’arrêt.|

 Affichage du code source à un point d’arrêt vous oblige à implémenter les méthodes de [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) et / ou les méthodes de [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).

## <a name="see-also"></a>Voir aussi
- [Contrôle des exécutions et évaluation de l’État](../../extensibility/debugger/execution-control-and-state-evaluation.md)
