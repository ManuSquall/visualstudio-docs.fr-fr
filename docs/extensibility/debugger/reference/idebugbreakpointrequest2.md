---
title: IDebugBreakpointRequest2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f30f9698c9c81322edd6935b40c16cad6f46024c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734914"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
Cette interface représente les informations nécessaires pour créer et lier n’importe quel type de point d’arrêt.

## <a name="syntax"></a>Syntaxe

```
IDebugBreakpointRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le gestionnaire de débogé de session (SDM) implémente généralement cette interface.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le moteur de débogé (DE) reçoit cette interface par le biais d’un appel pour [créerPendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) afin de créer un point d’arrêt en attente. Un appel à [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) peut récupérer cette interface à partir de la DE.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugBreakpointRequest2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Obtient le type de localisation de point de rupture de cette demande de point d’arrêt.|
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Obtient les informations de demande de point d’arrêt qui décrit cette demande de point d’arrêt.|

## <a name="remarks"></a>Notes
 Une fois que le programme a été déboqué, un appel à [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) lie un point d’arrêt en attente à l’emplacement demandé dans le programme.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)
- [Lier](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
