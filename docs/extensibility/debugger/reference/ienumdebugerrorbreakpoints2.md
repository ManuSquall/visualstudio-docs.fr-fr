---
title: IEnumDebugErrorBreakpoints2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d204b29b46e257d4ca0b8c4102c3a64e9e78adf1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317229"
---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
Cette interface énumère les points d’arrêt de l’erreur associées à un point d’arrêt en attente.

## <a name="syntax"></a>Syntaxe

```
IEnumDebugErrorBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Le moteur de débogage (dé) implémente cette interface dans le cadre de sa prise en charge des points d’arrêt.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Les appels de Visual Studio [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) pour obtenir cette interface représentant une liste de points d’arrêt ne peut pas être lié, ou [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) pour obtenir cette interface représentant une liste de points d’arrêt qui n’étaient pas liés.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IEnumDebugErrorBreakpoints2`.

|Méthode|Description|
|------------|-----------------|
|[Next](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|Récupère un nombre spécifié de points d’arrêt de l’erreur dans une séquence d’énumération.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|Ignore un nombre spécifié de points d’arrêt de l’erreur dans une séquence d’énumération.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|Réinitialise une séquence d’énumération au début.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur en cours.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|Obtient le nombre de points d’arrêt de l’erreur dans un énumérateur.|

## <a name="remarks"></a>Notes
 Cette interface conserve une liste de [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) interfaces, chacun d'entre eux décrivant un point d’arrêt qui ne peut pas être lié et pourquoi il ne peut pas être lié. Visual Studio utilise le `IEnumDebugErrorBreakpoint2` interface pour mettre à jour les points d’arrêt indiqués dans l’IDE.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)