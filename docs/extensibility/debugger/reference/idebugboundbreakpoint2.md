---
title: IDebugBoundBreakpoint2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da29303059558a4cf43eddb1d6e03e8848df4f4c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62877204"
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
Cette interface représente un point d’arrêt est lié à un emplacement de code.

## <a name="syntax"></a>Syntaxe

```
IDebugBoundBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Le moteur de débogage (dé) implémente cette interface dans le cadre de sa prise en charge des points d’arrêt.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Un appel à [lier](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) crée cette interface. Les appels à [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) et [suivant](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) peut également obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugBoundBreakpoint2`.

|Méthode|Description|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Obtient le point d’arrêt en attente à partir duquel le point d’arrêt lié spécifié a été créé.|
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Obtient l’état de ce point d’arrêt lié.|
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Obtient le nombre d’accès actuel pour ce point d’arrêt lié.|
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Obtient la résolution de point d’arrêt qui décrit ce point d’arrêt.|
|[Enable](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Active ou désactive le point d’arrêt.|
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Définit le nombre d’accès pour ce point d’arrêt lié.|
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Définit ou modifie la condition associée à ce point d’arrêt lié.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Jeux ou modifier le nombre de passe associé à ce point d’arrêt lié.|
|[Supprimer](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Supprime le point d'arrêt.|

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)
- [Next](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)
- [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)