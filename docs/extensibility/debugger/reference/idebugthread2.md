---
title: IDebugThread2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1965ff1b4cfa89e4584c194942dec7ae486473ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718584"
---
# <a name="idebugthread2"></a>IDebugThread2
Cette interface représente un thread qui s’exécute dans un programme.

## <a name="syntax"></a>Syntaxe

```
IDebugThread2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogage (DE) implémente cette interface pour représenter un thread d’exécution dans un programme unique.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appelez [GetThread,](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) pour obtenir cette interface représentant le thread actuellement actif.

 Cette interface est également utilisée pour la création d’une demande de point d’arrêt (voir [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)).

 Cette interface est également retournée lors de la résolution d’un point d’arrêt lié ou d’erreur (consultez [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) et [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)).

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugThread2` .

|Méthode|Description|
|------------|-----------------|
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|Récupère une liste des frames de pile pour ce thread.|
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|Obtient le nom du thread.|
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|Définit le nom du thread.|
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|Obtient le programme dans lequel un thread s’exécute.|
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Détermine si l’instruction suivante peut être définie sur le frame de pile et le contexte de code spécifiés.|
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Définit l’instruction suivante sur le frame de pile et le contexte de code spécifiés.|
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Obtient l’identificateur de thread système.|
|[Suspendre](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|Interrompt un thread.|
|[Reprendre](../../../extensibility/debugger/reference/idebugthread2-resume.md)|Reprend un thread.|
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|Obtient les propriétés qui décrivent un thread.|
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Obtient le thread logique associé à ce thread physique.|

## <a name="remarks"></a>Notes
 Étant donné qu’un seul thread physique peut s’exécuter dans plusieurs programmes, plusieurs `IDebugThread2` d’entre eux peuvent représenter le même thread physique.

 Lorsqu’un point d’arrêt ou une exception se produit, un événement est envoyé en appelant l' [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md). L’un des arguments de cette méthode est une `IDebugThread2` interface qui représente le thread actuel. [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) est utilisé pour obtenir l’interface [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) pour le frame de pile actuel.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
