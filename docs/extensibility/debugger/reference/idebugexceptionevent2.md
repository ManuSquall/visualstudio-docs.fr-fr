---
title: IDebugExceptionEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5c09b81a6a3eb56734e7d3a95dc5d1a8d1717fba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933113"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
Le moteur DE débogage (DE) envoie cette interface au gestionnaire de débogage de session (SDM) lorsqu’une exception est levée dans le programme en cours d’exécution.

## <a name="syntax"></a>Syntaxe

```
IDebugExceptionEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le DE implémente cette interface pour signaler qu’une exception s’est produite dans le programme en cours de débogage. L’interface [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) doit être implémentée sur le même objet que cette interface. Le SDM utilise [QueryInterface](/cpp/atl/queryinterface) pour accéder à l' `IDebugEvent2` interface.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le DE crée et envoie cet objet d’événement pour signaler une exception. L’événement est envoyé à l’aide de la fonction de rappel [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fournie par le SDM lorsqu’il est attaché au programme en cours de débogage.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugExceptionEvent2` .

|Méthode|Description|
|------------|-----------------|
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Obtient des informations détaillées sur l’exception qui a déclenché cet événement.|
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Obtient une description explicite de l’exception levée qui a déclenché cet événement.|
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Détermine si le moteur de débogage (DE) prend en charge l’option de passage de cette exception au programme en cours de débogage au moment de la reprise de l’exécution.|
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Spécifie si l’exception doit être passée au programme en cours de débogage au moment de la reprise de l’exécution ou si l’exception doit être ignorée.|

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Notes
 Avant d’envoyer l’événement, le DE vérifie si cet événement d’exception a été désigné comme une exception de première chance ou de seconde chance par un appel précédent à [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md). S’il a été désigné comme étant une exception de première chance, l' `IDebugExceptionEvent2` événement est envoyé au SDM. Si ce n’est pas le cas, le DE donne à l’application la possibilité de gérer l’exception. Si aucun gestionnaire d’exceptions n’est fourni et si l’exception a été désignée comme une deuxième chance, l' `IDebugExceptionEvent2` événement est envoyé au SDM. Dans le cas contraire, le DE reprend l’exécution du programme et le système d’exploitation ou le Runtime gère l’exception.

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
