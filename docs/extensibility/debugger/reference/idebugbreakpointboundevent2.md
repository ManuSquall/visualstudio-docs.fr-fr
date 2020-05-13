---
title: IDebugBreakpointBoundEvent2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointBoundEvent2
helpviewer_keywords:
- IDebugBreakpointBoundEvent2
ms.assetid: 24ba362e-5be1-481a-b071-e1ebd3cae6e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7943addb4334710da3252a4d822330e45b6e0f80
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735308"
---
# <a name="idebugbreakpointboundevent2"></a>IDebugBreakpointBoundEvent2
Cette interface indique au gestionnaire de débogé de session (SDM) qu’un point d’arrêt en attente a été lié avec succès à un programme chargé.

## <a name="syntax"></a>Syntaxe

```
IDebugBreakpointBoundEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE implémente cette interface dans le cadre de son support pour les points de rupture. [L’interface IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette `IDebugEvent2` interface (le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à l’interface).

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le DE crée et envoie cet objet d’événement lorsqu’un point d’arrêt en attente est lié avec succès au débugged du programme. L’événement est envoyé en utilisant la fonction de rappel [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu’elle s’est jointe au programme en cours de débbugged.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugBreakpointBoundEvent2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)|Obtient le point d’arrêt en attente qui est lié.|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)|Crée un enumérateur de points d’arrêt qui ont été liés sur cet événement.|

## <a name="remarks"></a>Notes
 Chaque fois qu’un point d’arrêt est lié, un événement est envoyé au SDM. Si le point d’arrêt ne peut pas être lié, un [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) est envoyé; autrement, `IDebugBreakpointBoundEvent2` un est envoyé.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
