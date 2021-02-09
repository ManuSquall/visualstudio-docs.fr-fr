---
title: IDebugPendingBreakpoint2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b6798d940bb186e6d685f22282e641eb2e690e48
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877406"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
Cette interface représente un point d’arrêt qui est prêt à être lié à un emplacement de code.

## <a name="syntax"></a>Syntaxe

```
IDebugPendingBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogage (DE) implémente cette interface dans le cadre de sa prise en charge des points d’arrêt.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Un appel à [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) crée un point d’arrêt en attente à partir d’une interface [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) . Un appel à [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) crée une `IDebugBreakpoint2` interface qui représente un point d’arrêt lié dans le programme.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugPendingBreakpoint2` .

|Méthode|Description|
|------------|-----------------|
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Détermine si ce point d’arrêt en attente peut être lié à un emplacement de code.|
|[Établis](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Lie ce point d’arrêt en attente à un ou plusieurs emplacements de code.|
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Obtient l’état de ce point d’arrêt en attente.|
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Obtient la demande de point d’arrêt qui a été utilisée pour créer ce point d’arrêt en attente.|
|[Virtualiser](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Active/désactive l’État virtualisé de ce point d’arrêt en attente.|
|[Activer](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Active/désactive l’état activé de ce point d’arrêt en attente.|
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Définit ou modifie la condition associée à ce point d’arrêt en attente.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Définit ou modifie le nombre de tests associés à ce point d’arrêt en attente.|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Énumère tous les points d’arrêt liés à ce point d’arrêt en attente.|
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Énumère tous les points d’arrêt d’erreur qui résultent de ce point d’arrêt en attente.|
|[Supprimer](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Supprime ce point d’arrêt en attente et tous les points d’arrêt liés à celui-ci.|

## <a name="remarks"></a>Remarques
 `IDebugPendingBreakpoint2` peut être considéré comme un fournisseur de toutes les informations nécessaires pour lier un point d’arrêt à du code qui peut être appliqué à un ou plusieurs programmes.

 Un point d’arrêt en attente peut potentiellement produire plus d’un point d’arrêt lié. Par exemple, un point d’arrêt dans un modèle de style C++ peut produire un point d’arrêt lié pour chaque instance unique de ce modèle.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)
