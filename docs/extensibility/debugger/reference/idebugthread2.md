---
title: IDebugThread2 - France Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718584"
---
# <a name="idebugthread2"></a>IDebugThread2
Cette interface représente un fil en cours d’exécution dans un programme.

## <a name="syntax"></a>Syntaxe

```
IDebugThread2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogé (DE) implémente cette interface pour représenter un fil d’exécution dans un seul programme.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appelez [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) pour obtenir cette interface représentant le thread actuellement actif.

 Cette interface est également utilisée dans la création d’une demande de point d’arrêt (voir [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)).

 Cette interface est également retournée lors de la résolution d’un point de rupture lié ou d’erreur (voir [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) et [BP_ERROR_RESOLUTION_INFO).](../../../extensibility/debugger/reference/bp-error-resolution-info.md)

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugThread2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|Récupère une liste des cadres de pile pour ce thread.|
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|Obtient le nom du thread.|
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|Définit le nom du fil.|
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|Obtient le programme dans lequel un thread est en cours d’exécution.|
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Détermine si la prochaine instruction peut être définie dans le cadre et le contexte du code de pile donnés.|
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Définit la déclaration suivante dans le cadre et le contexte de code donnés.|
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Obtient l’identifiant de thread système.|
|[Suspendre](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|Suspend un fil.|
|[Reprendre](../../../extensibility/debugger/reference/idebugthread2-resume.md)|Reprend un fil.|
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|Obtient des propriétés qui décrivent un thread.|
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Obtient le fil logique associé à ce fil physique.|

## <a name="remarks"></a>Notes
 Parce qu’un seul thread physique peut `IDebugThread2` fonctionner dans plusieurs programmes, plus d’un de plus d’un programme peut représenter le même fil physique.

 Lorsqu’un point d’arrêt ou une exception se produit, un événement est envoyé en appelant [l’événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md). Un des arguments de cette `IDebugThread2` méthode est une interface représentant le thread actuel. [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) est utilisé pour obtenir l’interface [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) pour le cadre de pile actuel.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
