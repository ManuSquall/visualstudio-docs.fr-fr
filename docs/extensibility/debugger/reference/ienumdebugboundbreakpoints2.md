---
title: IEnumDebugBoundBreakpoints2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 421d46efbef189fd6ffc86812d2bfdd28f5da5ff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717445"
---
# <a name="ienumdebugboundbreakpoints2"></a>IEnumDebugBoundBreakpoints2
Cette interface énumère les points de rupture liés associés à un point de rupture en attente ou un événement lié au point d’arrêt.

## <a name="syntax"></a>Syntaxe

```
IEnumDebugBoundBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogé (DE) implémente cette interface dans le cadre de son support pour les points de rupture. Cette interface doit être implémentée si les points d’arrêt sont pris en charge.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appels Visual Studio :

- [EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) pour obtenir cette interface représentant une liste de tous les points de rupture qui ont été déclenchés.

- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) pour obtenir cette interface représentant une liste de tous les points d’arrêt qui étaient liés.

- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) pour obtenir cette interface représentant une liste de tous les points d’arrêt liés à ce point d’arrêt en attente.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IEnumDebugBoundBreakpoints2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[Suivant](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|Récupère un nombre précis de points d’arrêt liés dans une séquence de recensement.|
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|Passe un nombre spécifié de points de rupture liés dans une séquence de recensement.|
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|Réinitialise une séquence d'énumération.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|Crée un enumérateur qui contient le même état de recensement que l’enumérateur actuel.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|Obtient le nombre de points d’arrêt liés dans un enumérateur.|

## <a name="remarks"></a>Notes
 Visual Studio utilise les points de rupture liés représentés par cette interface pour mettre à jour l’affichage des points d’arrêt dans l’IDE.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
