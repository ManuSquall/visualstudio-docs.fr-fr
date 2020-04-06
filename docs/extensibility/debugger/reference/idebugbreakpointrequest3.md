---
title: IDebugBreakpointRequest3 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 505b0c0b05fa0f14578d770abec6c43ed6b80b01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734821"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
Cette interface représente les informations nécessaires pour créer et lier n’importe quel type de point d’arrêt. Il s’agit d’une extension de [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).

## <a name="syntax"></a>Syntaxe

```
IDebugBreakpointRequest3 : IDebugBreakpointRequest2
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le gestionnaire de débogé de session (SDM) implémente généralement cette interface.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le moteur de déboçon (DE) accède à cette interface en appelant [QueryInterface](/cpp/atl/queryinterface) sur l’interface IDebugBreakpointRequest2 reçue dans un appel pour [créerPendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 En plus des méthodes héritées de [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md), l’interface `IDebugBreakpointRequest3` expose la méthode suivante.

|Méthode|Description|
|------------|-----------------|
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Obtient les informations de demande de point d’arrêt qui décrit cette demande de point d’arrêt.|

## <a name="remarks"></a>Notes
 Cette interface est utilisée pour fournir des informations supplémentaires à la DE à travers la structure [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md) Ces informations supplémentaires comprennent l’ID du fournisseur de DE (sous la forme d’un GUID), le nom d’un point de trace, et le nom d’une contrainte de point d’arrêt.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
