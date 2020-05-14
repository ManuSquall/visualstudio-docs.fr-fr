---
title: IDebugExceptionEvent2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbd53d56b21886e972b33c219367edd603cbf0d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729781"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
Le moteur de débogé (DE) envoie cette interface au gestionnaire de débogé de session (SDM) lorsqu’une exception est lancée dans le programme actuellement exécuté.

## <a name="syntax"></a>Syntaxe

```
IDebugExceptionEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE implémente cette interface pour signaler qu’une exception s’est produite dans le programme étant débogé. [L’interface IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface. Le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à l’interface. `IDebugEvent2`

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le DE crée et envoie cet objet d’événement pour signaler une exception. L’événement est envoyé à l’aide de la fonction de rappel [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) qui est fournie par le SDM lorsqu’il est attaché au programme étant débogé.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugExceptionEvent2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Obtient des informations détaillées sur l’exception qui a déclenché cet événement.|
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Obtient une description lisible par l’homme pour l’exception jetée qui a tiré cet événement.|
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Détermine si le moteur de débogé (DE) prend en charge la possibilité de passer cette exception au programme qui est débogé lorsque l’exécution reprend.|
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Précise si l’exception doit être transmise au programme qui est débogé lorsque l’exécution reprend, ou si l’exception doit être écartée.|

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Notes
 Avant d’envoyer l’événement, le DE vérifie si cet événement d’exception a été désigné une exception de première chance ou de seconde chance par un appel précédent à [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md). S’il a été désigné comme une `IDebugExceptionEvent2` exception de première chance, l’événement est envoyé au SDM. Si ce n’est pas le cas, le DE donne à l’application une chance de gérer l’exception. Si aucun gestionnaire d’exception n’est fourni et si l’exception a été désignée comme une exception de deuxième chance, l’événement `IDebugExceptionEvent2` est envoyé au SDM. Dans le cas contraire, le DE reprend l’exécution du programme, et le système d’exploitation ou le temps d’exécution gère l’exception.

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
