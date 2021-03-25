---
description: L’interface IDebugBreakpointRequest3 représente les informations nécessaires à la création et à la liaison de tout type de point d’arrêt.
title: IDebugBreakpointRequest3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6803b62975822f1b5219caa43844c8983303a998
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054411"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
Cette interface représente les informations nécessaires à la création et à la liaison de tout type de point d’arrêt. Il s’agit d’une extension de [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).

## <a name="syntax"></a>Syntaxe

```
IDebugBreakpointRequest3 : IDebugBreakpointRequest2
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le gestionnaire de débogage de session (SDM) implémente généralement cette interface.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le moteur DE débogage (DE) accède à cette interface en appelant [QueryInterface](/cpp/atl/queryinterface) sur l’interface IDebugBreakpointRequest2 reçue dans un appel à [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 En plus des méthodes héritées de [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md), l' `IDebugBreakpointRequest3` interface expose la méthode suivante.

|Méthode|Description|
|------------|-----------------|
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Obtient les informations de demande de point d’arrêt qui décrivent cette demande de point d’arrêt.|

## <a name="remarks"></a>Notes
 Cette interface est utilisée pour fournir des informations supplémentaires au par le biais de la structure [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) . Ces informations supplémentaires incluent l’ID de fournisseur DE l’éditeur (sous la forme d’un GUID), le nom d’un point de trace et le nom d’une contrainte de point d’arrêt.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
