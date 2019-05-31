---
title: IDebugExceptionEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3fd2a449c71b69c654cd19846990f7b722f706de
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325990"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
Le moteur de débogage (dé) envoie cette interface pour le Gestionnaire de session de débogage (SDM) lorsqu’une exception est levée dans le programme en cours d’exécution.

## <a name="syntax"></a>Syntaxe

```
IDebugExceptionEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Le D’implémente cette interface à signaler qu’une exception s’est produite dans le programme en cours de débogage. Le [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface doit être implémentée sur le même objet que cette interface. Utilise le SDM [QueryInterface](/cpp/atl/queryinterface) pour accéder à la `IDebugEvent2` interface.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Le DE crée et envoie cet objet d’événement pour signaler une exception. L’événement est envoyé à l’aide de la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fonction de rappel qui est fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugExceptionEvent2`.

|Méthode|Description|
|------------|-----------------|
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Obtient des informations détaillées relatives à l’exception qui a déclenché cet événement.|
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Obtient une description explicite de l’exception levée qui a déclenché cet événement.|
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Détermine si le moteur de débogage (dé) prend en charge la possibilité de transmettre cette exception au programme en cours de débogage lors de l’exécution reprend.|
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Spécifie si l’exception doit être passée le programme en cours de débogage lors de l’exécution reprend, ou si l’exception doit être ignorée.|

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Notes
 Avant d’envoyer l’événement, le DE vérifie si cet événement d’exception a été désigné une exception de première chance ou de la seconde chance par un appel précédent à [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md). S’il a été désigné pour être une exception de première chance, la `IDebugExceptionEvent2` événement est envoyé au SDM. Si ce n’est pas le cas, le DE donne une chance de traiter l’exception à l’application. Si aucun gestionnaire d’exceptions n’est fourni, et si l’exception a été désignée comme une exception de la seconde chance, les `IDebugExceptionEvent2` événement est envoyé au SDM. Sinon, l’Allemagne reprend l’exécution du programme, et le système d’exploitation ou le runtime gère l’exception.

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)