---
description: Cette interface est utilisée pour communiquer les informations de débogage critiques, telles que l’arrêt à un point d’arrêt et les informations non critiques, telles qu’un message de débogage.
title: IDebugEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f5406c70703b594236dba47539e5cc76bbe67a73
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065760"
---
# <a name="idebugevent2"></a>IDebugEvent2
Cette interface est utilisée pour communiquer les informations de débogage critiques, telles que l’arrêt à un point d’arrêt et les informations non critiques, telles qu’un message de débogage.

## <a name="syntax"></a>Syntaxe

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur DE débogage (DE) et le fournisseur de port personnalisé implémentent cette interface sur le même objet que toutes les autres interfaces d’événements.

## <a name="notes-for-callers"></a>Notes pour les appelants
 À l’aide de l’argument d’ID d’interface (IID) donné à l' [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ou à l' [événement](../../../extensibility/debugger/reference/idebugportevents2-event.md), le gestionnaire de débogage de session (SDM) appelle [QueryInterface](/cpp/atl/queryinterface) sur l' `IDebugEvent2` interface pour obtenir l’interface d’événement appropriée.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugEvent2` .

|Méthode|Description|
|------------|-----------------|
|[GetAttributes,](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Obtient les attributs de cet événement de débogage.|

## <a name="remarks"></a>Notes
 Les interfaces d’événements plus spécifiques, telles que [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), ne dérivent pas de l’interface IDebugEvent2, mais elles sont implémentées en tant qu’interface distincte sur le même objet que `IDebugEvent2` .

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
