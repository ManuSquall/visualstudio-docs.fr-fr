---
title: IDebugEventCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d8d05ea232513a161b3123e08a20bc0f5b312b89
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920284"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
Cette interface est utilisée par le moteur de débogage (dé) pour envoyer des événements de débogage pour le Gestionnaire de session de débogage (SDM).

## <a name="syntax"></a>Syntaxe

```
IDebugEventCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] implémente cette interface pour recevoir des événements à partir d’un moteur de débogage.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Un moteur de débogage reçoit généralement cette interface lorsque le SDM appelle [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md), ou [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Un moteur de débogage envoie des événements pour le SDM en appelant [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugEventCallback2`.

|Méthode|Description|
|------------|-----------------|
|[Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Envoie une notification de débogage des événements pour le SDM.|

## <a name="remarks"></a>Notes
 Bien que [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) et [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) spécifier qu’ils prennent une `IDebugEventCallback2` interface, cela n’est pas le cas, et le pointeur d’interface sera toujours une valeur null. Au lieu de cela, le moteur de débogage doit utiliser le `IDebugEventCallback2` reçus dans l’appel à interface [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md), ou [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

 Si un package implémente [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) en code managé, il est fortement recommandé que <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> appelée sur les diverses interfaces qui sont passées à [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Attacher](../../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md)