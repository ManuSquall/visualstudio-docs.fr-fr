---
title: IDebugEvent2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6341f8003b962a7f45420b076b23623ebdaf861
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729914"
---
# <a name="idebugevent2"></a>IDebugEvent2
Cette interface est utilisée pour communiquer à la fois des informations de déboguer critiques, telles que l’arrêt à un point d’arrêt, et des informations non critiques, telles qu’un message de débogage.

## <a name="syntax"></a>Syntaxe

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogé (DE) et le fournisseur de porto personnalisé implémentent cette interface sur le même objet que toutes les autres interfaces d’événements.

## <a name="notes-for-callers"></a>Notes pour les appelants
 À l’aide de l’argument de l’interface ID (IID) donné à [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) or `IDebugEvent2` [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md), le gestionnaire de débogé de session (SDM) appelle [QueryInterface](/cpp/atl/queryinterface) sur l’interface pour obtenir l’interface d’événement appropriée.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugEvent2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Obtient les attributs pour cet événement de débogé.|

## <a name="remarks"></a>Notes
 Les interfaces d’événements plus spécifiques, telles que [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), ne dérivent pas de l’interface IDebugEvent2 mais sont plutôt implémentées comme une interface distincte sur le même objet que `IDebugEvent2`.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [Événement](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
