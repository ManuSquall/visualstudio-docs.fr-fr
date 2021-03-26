---
description: Cette interface notifie un écouteur (en général, le gestionnaire de débogage de session [SDM] ou un moteur de débogage) de la création et de la destruction des processus et des programmes sur un port particulier.
title: IDebugPortEvents2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d8e1ccbb2726fb0f90fae2d31a4b07daad9bae91
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065383"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
Cette interface notifie un écouteur (en général, le gestionnaire de débogage de session [SDM] ou un moteur de débogage) de la création et de la destruction des processus et des programmes sur un port particulier. Ces informations peuvent être utilisées pour présenter une vue en temps réel des processus et des programmes en cours d’exécution sur le port.

## <a name="syntax"></a>Syntaxe

```
IDebugPortEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Visual Studio implémente généralement cette interface pour recevoir des notifications sur la création et la destruction d’un programme. Un moteur de débogage peut également implémenter cette interface pour écouter ces événements de port.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Toutes les interfaces [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) peuvent être interrogées pour une <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interface. Ensuite, la <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> méthode de `IDebugPortEvents2` est appelée dans l' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interface pour obtenir une <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interface. Enfin, la <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> méthode dans l' <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interface est appelée pour envoyer les événements via la méthode d' [événement](../../../extensibility/debugger/reference/idebugportevents2-event.md) .

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant illustre la méthode de `IDebugPortEvents2` .

|Méthode|Description|
|------------|-----------------|
|[Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Envoie des événements qui décrivent la création et la destruction des processus et des programmes sur le port.|

## <a name="remarks"></a>Notes
 `IDebugPortEvents2` est également utilisé par le SDM pour déboguer des programmes qui s’exécutent dans un processus qui est déjà en cours de débogage.

 Les événements de port sont passés au SDM par cette interface.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
