---
title: IDebugBreakpointRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 55e7c73b720e326b823c3038928d7141ea732155
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352922"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
Cette interface représente les informations nécessaires pour créer et lier n’importe quel type de point d’arrêt.

## <a name="syntax"></a>Syntaxe

```
IDebugBreakpointRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 En général, le Gestionnaire de session de débogage (SDM) implémente cette interface.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Le moteur de débogage (dé) reçoit cette interface via un appel à [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) afin de créer un point d’arrêt en attente. Un appel à [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) peut récupérer cette interface à partir de l’Allemagne.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugBreakpointRequest2`.

|Méthode|Description|
|------------|-----------------|
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Obtient le type d’emplacement de point d’arrêt de cette demande de point d’arrêt.|
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Obtient les informations de demande de point d’arrêt qui décrit cette demande de point d’arrêt.|

## <a name="remarks"></a>Notes
 Une fois le programme en cours de débogage a été chargé, un appel à [lier](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) lie un point d’arrêt en attente à l’emplacement demandé dans le programme.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)
- [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)