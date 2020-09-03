---
title: IDebugPropertyCreateEvent2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80720934"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
Cette interface est envoyée par le moteur de débogage (DE) au gestionnaire de débogage de session (SDM) lorsqu’elle crée une propriété associée à un document spécifique.

## <a name="syntax"></a>Syntaxe

```
IDebugPropertyCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE implémente cette interface pour signaler qu’une propriété a été créée. L’interface [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface. Le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à l' `IDebugEvent2` interface. Cette interface est implémentée si le DE a créé une propriété associée à un script qui a été chargé ou créé et si ce script doit apparaître dans l’IDE.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le DE crée et envoie cet objet d’événement pour signaler qu’une propriété a été créée. L’événement est envoyé à l’aide de la fonction de rappel [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre la méthode de l' `IDebugPropertyCreateEvent2` interface.

|Méthode|Description|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Obtient la nouvelle propriété.|

## <a name="remarks"></a>Notes
 Si un document ou un script spécifique est associé à une propriété, le DE peut envoyer cet événement au SDM afin de mettre à jour la fenêtre **documents de script** avec le nom du document. Le SDM appellera [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) avec l’argument `guidDocument` pour récupérer un `VARIANT` contenant un pointeur [IUnknown](/cpp/atl/iunknown) . Le SDM appellera [QueryInterface](/cpp/atl/queryinterface) sur ce pointeur pour récupérer l’interface [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) utilisée pour mettre à jour la fenêtre **documents de script** .

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
