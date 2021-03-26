---
description: Cette interface représente un point d’arrêt qui est lié à un emplacement de code.
title: IDebugBoundBreakpoint2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b8a48ffcb3c0409839ec9323679e396a7e23b8f3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088820"
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
Cette interface représente un point d’arrêt qui est lié à un emplacement de code.

## <a name="syntax"></a>Syntaxe

```
IDebugBoundBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogage (DE) implémente cette interface dans le cadre de sa prise en charge des points d’arrêt.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Un appel à [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) crée cette interface. Les appels à [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) et [Next](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) peuvent également obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugBoundBreakpoint2` .

|Méthode|Description|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Obtient le point d’arrêt en attente à partir duquel le point d’arrêt lié spécifié a été créé.|
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Obtient l’état de ce point d’arrêt lié.|
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Obtient le nombre d’accès actuel pour ce point d’arrêt lié.|
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Obtient la résolution de point d’arrêt qui décrit ce point d’arrêt.|
|[Activer](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Active ou désactive le point d’arrêt.|
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Définit le nombre d’accès pour ce point d’arrêt lié.|
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Définit ou modifie la condition associée à ce point d’arrêt lié.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Définit ou modifie le nombre de tests associés à ce point d’arrêt lié.|
|[Supprimer](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Supprime le point d'arrêt.|

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)
- [Next](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)
- [Établis](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
