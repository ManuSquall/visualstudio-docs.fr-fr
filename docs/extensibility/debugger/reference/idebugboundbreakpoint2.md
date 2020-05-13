---
title: IDebugBoundBreakpoint2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4d22b10085baefeb3a0286c1b4edcb5876c0dac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735425"
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
Cette interface représente un point d’arrêt lié à un emplacement de code.

## <a name="syntax"></a>Syntaxe

```
IDebugBoundBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogé (DE) implémente cette interface dans le cadre de son support pour les points de rupture.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Un appel à [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) crée cette interface. Les appels vers [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) et [Next](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) peuvent également obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugBoundBreakpoint2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Obtient le point d’arrêt en attente à partir duquel le point de rupture lié spécifié a été créé.|
|[GetState (en)](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Obtient l’état de ce point de rupture lié.|
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Obtient le nombre de coups en cours pour ce point d’arrêt lié.|
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Obtient la résolution de point d’arrêt qui décrit ce point d’arrêt.|
|[Activer](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Permet ou désactive le point d’arrêt.|
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Définit le nombre de coups pour ce point d’arrêt lié.|
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Définit ou modifie la condition associée à ce point de rupture lié.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Définit ou modifie le nombre de laissez-passer associé à ce point de rupture lié.|
|[Supprimer](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Supprime le point d'arrêt.|

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)
- [Suivant](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)
- [Lier](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
