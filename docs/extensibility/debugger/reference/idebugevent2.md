---
title: IDebugEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f87184481c5d01e74d284b175078b67f6f2612d1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310596"
---
# <a name="idebugevent2"></a>IDebugEvent2
Cette interface est utilisée pour communiquer des informations de débogage critiques, tels que l’arrêt à un point d’arrêt et les informations non critiques, par exemple, un message de débogage.

## <a name="syntax"></a>Syntaxe

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Le moteur de débogage (dé) et le fournisseur de port personnalisé implémentent cette interface sur le même objet en tant que toutes les autres interfaces d’événement.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 À l’aide de l’interface argument ID (IID) donné à [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ou [événement](../../../extensibility/debugger/reference/idebugportevents2-event.md), appelle le Gestionnaire de session de débogage (SDM) [QueryInterface](/cpp/atl/queryinterface) sur la `IDebugEvent2` interface à obtenir l’interface d’événements approprié.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugEvent2`.

|Méthode|Description|
|------------|-----------------|
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Obtient les attributs de cet événement de débogage.|

## <a name="remarks"></a>Notes
 Interfaces de l’événement plus spécifique, tel que [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), ne dérivent pas de l’interface IDebugEvent2 mais sont plutôt implémentées comme une interface distincte sur le même objet en tant que `IDebugEvent2`.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)