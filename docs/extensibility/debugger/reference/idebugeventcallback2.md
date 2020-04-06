---
title: IDebugEventCallback2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a74825a955afdde03e63673c4b1b6afda5904953
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729890"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
Cette interface est utilisée par le moteur de débogé (DE) pour envoyer des événements de débog au gestionnaire de débog de session (SDM).

## <a name="syntax"></a>Syntaxe

```
IDebugEventCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]implémente cette interface pour recevoir des événements d’un moteur de débogé.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Un moteur de débogé reçoit généralement cette interface lorsque le SDM appelle [Attacher,](../../../extensibility/debugger/reference/idebugprogram2-attach.md) [Joindre](../../../extensibility/debugger/reference/idebugengine2-attach.md), ou [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Un moteur de débogé envoie des événements à la SDM en appelant [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugEventCallback2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Envoie une notification des événements de débogage au SDM.|

## <a name="remarks"></a>Notes
 Bien que [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) et [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) spécifier qu’ils prennent une interface, ce n’est `IDebugEventCallback2` pas le cas, et le pointeur d’interface sera toujours une valeur nulle. Au lieu de cela, le `IDebugEventCallback2` moteur de débogé doit utiliser l’interface reçue dans l’appel à [Attacher](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md), ou [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

 Si un paquet implémente [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) dans <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> le code géré, il est fortement conseillé d’être invoqué sur les différentes interfaces qui sont transmises à [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
