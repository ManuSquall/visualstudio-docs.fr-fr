---
title: IDebugPropertyCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3c5afdd5b1c3c8eaf62f9cd15ab2ea9474f9c040
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56706156"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
Cette interface est envoyée par le moteur de débogage (dé) pour le Gestionnaire de session de débogage (SDM) lorsqu’il crée une propriété qui est associée à un document spécifique.

## <a name="syntax"></a>Syntaxe

```
IDebugPropertyCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Le D’implémente cette interface pour signaler qu’une propriété a été créée. Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface doit être implémentée sur le même objet que cette interface. Utilise le SDM [QueryInterface](/cpp/atl/queryinterface) pour accéder à la `IDebugEvent2` interface. Cette interface est implémentée si le dé a créé une propriété associée à un script qui a été chargé ou créé et si ce script doit apparaître dans l’IDE.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Le DE crée et envoie cet objet d’événement à une propriété a été créée de rapport. L’événement est envoyé à l’aide de la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fonction de rappel qui est fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente la méthode de la `IDebugPropertyCreateEvent2` interface.

|Méthode|Description|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Obtient la nouvelle propriété.|

## <a name="remarks"></a>Notes
 Si une propriété a un document spécifique ou un script associé, l’Allemagne peut envoyer cet événement pour le SDM pour mettre à jour le **Documents de Script** fenêtre avec le nom du document. Le SDM appellera [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) avec l’argument `guidDocument` pour récupérer un `VARIANT` contenant un [IUnknown](/cpp/atl/iunknown) pointeur. Le SDM appellera [QueryInterface](/cpp/atl/queryinterface) sur ce pointeur pour récupérer le [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interface qui est utilisée pour mettre à jour le **Documents de Script** fenêtre.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)