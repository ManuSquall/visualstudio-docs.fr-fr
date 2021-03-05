---
description: Cette interface est utilisée par le moteur de débogage (DE) pour envoyer des événements de débogage au gestionnaire de débogage de session (SDM).
title: IDebugEventCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cb33bcbdff14b0f95aab5d8f300473c13d4c342f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152908"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
Cette interface est utilisée par le moteur de débogage (DE) pour envoyer des événements de débogage au gestionnaire de débogage de session (SDM).

## <a name="syntax"></a>Syntaxe

```
IDebugEventCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] implémente cette interface pour recevoir des événements d’un moteur de débogage.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Un moteur de débogage reçoit généralement cette interface lorsque le SDM appelle [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)ou [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Un moteur de débogage envoie des événements au SDM en appelant l' [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugEventCallback2` .

|Méthode|Description|
|------------|-----------------|
|[Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Envoie une notification d’événements de débogage au SDM.|

## <a name="remarks"></a>Notes
 Bien que [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) et [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) spécifient qu’ils prennent une `IDebugEventCallback2` interface, ce n’est pas le cas, et le pointeur d’interface est toujours une valeur null. Au lieu de cela, le moteur de débogage doit utiliser l' `IDebugEventCallback2` interface reçue dans l’appel d' [attachement](../../../extensibility/debugger/reference/idebugprogram2-attach.md), d' [attachement](../../../extensibility/debugger/reference/idebugengine2-attach.md)ou de [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

 Si un package implémente [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) dans du code managé, il est vivement recommandé de <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> l’appeler sur les différentes interfaces passées à l' [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Attacher](../../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md)
