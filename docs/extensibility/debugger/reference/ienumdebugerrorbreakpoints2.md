---
description: Cette interface énumère les points d’arrêt d’erreur associés à un point d’arrêt en attente.
title: IEnumDebugErrorBreakpoints2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 71667ef0de4d72d2d6db2619c41c68b7949803e8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086584"
---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
Cette interface énumère les points d’arrêt d’erreur associés à un point d’arrêt en attente.

## <a name="syntax"></a>Syntaxe

```
IEnumDebugErrorBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogage (DE) implémente cette interface dans le cadre de sa prise en charge des points d’arrêt.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Visual Studio appelle [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) pour obtenir cette interface représentant une liste de points d’arrêt qui ne peuvent pas être liés, ou [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) pour obtenir cette interface représentant une liste de points d’arrêt qui n’étaient pas liés.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IEnumDebugErrorBreakpoints2` .

|Méthode|Description|
|------------|-----------------|
|[Next](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|Récupère un nombre spécifié de points d’arrêt sur erreur dans une séquence d’énumération.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|Ignore un nombre spécifié de points d’arrêt sur erreur dans une séquence d’énumération.|
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|Réinitialise une séquence d'énumération.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|Obtient le nombre de points d’arrêt sur erreur dans un énumérateur.|

## <a name="remarks"></a>Notes
 Cette interface contient une liste d’interfaces [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) , chacune décrivant un point d’arrêt qui n’a pas pu être lié et la raison pour laquelle elle n’a pas pu être liée. Visual Studio utilise l' `IEnumDebugErrorBreakpoint2` interface pour mettre à jour les points d’arrêt affichés dans l’IDE.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
