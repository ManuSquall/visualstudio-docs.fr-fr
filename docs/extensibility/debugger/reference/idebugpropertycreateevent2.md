---
title: IDebugPropertyCreateEvent2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84d8fcb4375f29820b51752ac3fdebbd04f06f80
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720934"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
Cette interface est envoyée par le moteur de débogé (DE) au gestionnaire de débogé de session (SDM) lorsqu’elle crée une propriété associée à un document spécifique.

## <a name="syntax"></a>Syntaxe

```
IDebugPropertyCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE implémente cette interface pour signaler qu’une propriété a été créée. [L’interface IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface. Le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à l’interface. `IDebugEvent2` Cette interface est implémentée si le DE a créé une propriété associée à un script qui a été chargé ou créé et si ce script doit apparaître dans l’IDE.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le DE crée et envoie cet objet d’événement pour signaler qu’une propriété a été créée. L’événement est envoyé en utilisant la fonction de rappel [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) qui est fournie par le SDM lorsqu’il est attaché au programme en cours de débbugged.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugPropertyCreateEvent2` la méthode de l’interface.

|Méthode|Description|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Il a la nouvelle propri été.|

## <a name="remarks"></a>Notes
 Si une propriété dispose d’un document ou d’un script spécifique qui lui est associé, le DE peut envoyer cet événement au SDM afin de mettre à jour la fenêtre **Script Documents** avec le nom du document. Le SDM appellera [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) avec `guidDocument` `VARIANT` l’argument pour récupérer un pointeur contenant un pointeur [IUnknown.](/cpp/atl/iunknown) Le SDM appellera [QueryInterface](/cpp/atl/queryinterface) sur ce pointeur pour récupérer [l’interface IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) qui est utilisée pour mettre à jour la fenêtre **Script Documents.**

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
