---
title: IDebugBreakpointErrorEvent2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointErrorEvent2
helpviewer_keywords:
- IDebugBreakpointErrorEvent2
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09cb93f0f16420e56104f371d9caab262873390f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735045"
---
# <a name="idebugbreakpointerrorevent2"></a>IDebugBreakpointErrorEvent2
Cette interface indique au gestionnaire de débogé de session (SDM) qu’un point d’arrêt en attente ne pouvait pas être lié à un programme chargé, soit en raison d’un avertissement ou d’une erreur.

## <a name="syntax"></a>Syntaxe

```
IDebugBreakpointErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE implémente cette interface dans le cadre de son support pour les points de rupture. [L’interface IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette `IDebugEvent2` interface (le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à l’interface).

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le DE crée et envoie cet objet d’événement lorsqu’un point d’arrêt en attente ne peut pas être lié au débugged du programme. L’événement est envoyé en utilisant la fonction de rappel [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu’elle s’est jointe au programme en cours de débbugged.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugBreakpointErrorEvent2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|Obtient l’interface [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) qui décrit l’avertissement ou l’erreur.|

## <a name="remarks"></a>Notes
 Chaque fois qu’un point d’arrêt est lié, un événement est envoyé au SDM. Si le point d’arrêt `IDebugBreakpointErrorEvent2` ne peut pas être lié, un est envoyé; autrement, un [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) est envoyé.

 Par exemple, lorsque la condition associée au point d’arrêt en attente ne parvient pas à analyser ou à évaluer, un avertissement est envoyé que le point d’arrêt en attente ne peut pas être lié pour le moment. Cela peut se produire si le code du point d’arrêt n’a pas encore chargé.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
