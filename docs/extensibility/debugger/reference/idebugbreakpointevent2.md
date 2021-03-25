---
description: Le moteur DE débogage (DE) envoie cette interface au gestionnaire de débogage de session (SDM) lorsqu’un programme s’arrête à un point d’arrêt.
title: IDebugBreakpointEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointEvent2
helpviewer_keywords:
- IDebugBreakpointEvent2 interface
ms.assetid: 50b3a7a7-331b-42c8-922c-ff3522ebe1da
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 29dd8aa27c6b73d09036905a8c6e43af878419eb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054540"
---
# <a name="idebugbreakpointevent2"></a>IDebugBreakpointEvent2
Le moteur DE débogage (DE) envoie cette interface au gestionnaire de débogage de session (SDM) lorsqu’un programme s’arrête à un point d’arrêt.

## <a name="syntax"></a>Syntaxe

```
IDebugBreakpointEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE implémente cette interface dans le cadre de sa prise en charge des points d’arrêt. L’interface [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface (le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à l' `IDebugEvent2` interface).

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le DE crée et envoie cet objet d’événement lorsqu’au moins un point d’arrêt est rencontré dans le programme. L’événement est envoyé à l’aide de la fonction de rappel [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugBreakpointEvent2` .

|Méthode|Description|
|------------|-----------------|
|[EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)|Crée un énumérateur pour tous les points d’arrêt qui ont été déclenchés à l’emplacement de code actuel.|

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
