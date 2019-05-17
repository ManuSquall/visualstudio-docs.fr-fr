---
title: IDebugPendingBreakpoint2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 816fad53554675e7f29cef838d4ea24e154dca8c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62871932"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
Cette interface représente un point d’arrêt est prêt à lier à un emplacement de code.

## <a name="syntax"></a>Syntaxe

```
IDebugPendingBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Le moteur de débogage (dé) implémente cette interface dans le cadre de sa prise en charge des points d’arrêt.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Un appel à [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) crée un point d’arrêt en attente à partir d’un [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) interface. Un appel à [lier](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) crée un `IDebugBreakpoint2` interface qui représente un point d’arrêt lié dans le programme.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugPendingBreakpoint2`.

|Méthode|Description|
|------------|-----------------|
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Détermine si ce point d’arrêt en attente peut lier à un emplacement de code.|
|[Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Lie ce point d’arrêt en attente à un ou plusieurs emplacements de code.|
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Obtient l’état de ce point d’arrêt dans l’attente.|
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Obtient la demande de point d’arrêt a été utilisée pour créer ce point d’arrêt en attente.|
|[Virtualize](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Active ou désactive le virtualisé cela en attente de point d’arrêt.|
|[Enable](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Active ou désactive l’état activé de ce point d’arrêt dans l’attente.|
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Définit ou modifie la condition associée à cet en attente de point d’arrêt.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Définit ou modifie le nombre de passe associé à ce point d’arrêt dans l’attente.|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Énumère tous les points d’arrêt liés à partir de ce point d’arrêt en attente.|
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Énumère toutes les erreurs des points d’arrêt qui ont abouti à partir de ce point d’arrêt en attente.|
|[Supprimer](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Supprime ce point d’arrêt en attente et tous les points d’arrêt liés à partir de celui-ci.|

## <a name="remarks"></a>Notes
 `IDebugPendingBreakpoint2` peut être considéré comme un fournisseur de toutes les informations nécessaires pour lier un point d’arrêt au code qui peut être appliqué à un ou plusieurs programmes.

 Un point d’arrêt en attente peut produire plus d’un point d’arrêt lié. Par exemple, un point d’arrêt dans un modèle de style C++ peut générer un point d’arrêt lié pour chaque instance unique de ce modèle.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)