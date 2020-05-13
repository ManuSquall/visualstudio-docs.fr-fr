---
title: IDebugBreakpointEvent2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointEvent2
helpviewer_keywords:
- IDebugBreakpointEvent2 interface
ms.assetid: 50b3a7a7-331b-42c8-922c-ff3522ebe1da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f59bdef49f5c7b9c4dc345ba1862f3f08042428e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735014"
---
# <a name="idebugbreakpointevent2"></a>IDebugBreakpointEvent2
Le moteur de débogé (DE) envoie cette interface au gestionnaire de débogé de session (SDM) lorsqu’un programme s’arrête à un point d’arrêt.

## <a name="syntax"></a>Syntaxe

```
IDebugBreakpointEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE implémente cette interface dans le cadre de son support pour les points de rupture. [L’interface IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette `IDebugEvent2` interface (le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à l’interface).

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le DE crée et envoie cet objet d’événement lorsqu’au moins un point d’arrêt est rencontré dans le programme. L’événement est envoyé en utilisant la fonction de rappel [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu’elle s’est jointe au programme en cours de débbugged.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugBreakpointEvent2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)|Crée un enumérateur pour tous les points d’arrêt qui ont tiré à l’emplacement actuel du code.|

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
