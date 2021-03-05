---
description: L’interface IDebugBreakPointRequest2 représente les informations nécessaires à la création et à la liaison de tout type de point d’arrêt.
title: IDebugBreakpointRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7e7d13c945de1358265a5eb92769192ce736be49
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162353"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
Cette interface représente les informations nécessaires à la création et à la liaison de tout type de point d’arrêt.

## <a name="syntax"></a>Syntaxe

```
IDebugBreakpointRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le gestionnaire de débogage de session (SDM) implémente généralement cette interface.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le moteur DE débogage (DE) reçoit cette interface via un appel à [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) afin de créer un point d’arrêt en attente. Un appel à [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) peut récupérer cette interface à partir de la.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugBreakpointRequest2` .

|Méthode|Description|
|------------|-----------------|
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Obtient le type d’emplacement du point d’arrêt de cette demande de point d’arrêt.|
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Obtient les informations de demande de point d’arrêt qui décrivent cette demande de point d’arrêt.|

## <a name="remarks"></a>Notes
 Une fois que le programme en cours de débogage a été chargé, un appel à [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) lie un point d’arrêt en attente à l’emplacement demandé dans le programme.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)
- [Établis](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
