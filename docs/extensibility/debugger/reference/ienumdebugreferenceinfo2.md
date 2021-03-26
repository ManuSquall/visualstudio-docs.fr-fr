---
description: Cette interface énumère les structures de DEBUG_REFERENCE_INFO.
title: IEnumDebugReferenceInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 27917741d6110f2811b39587607b05cd0075f986
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082801"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
Cette interface énumère les structures de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) .

## <a name="syntax"></a>Syntaxe

```
IEnumDebugReferenceInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogage (DE) implémente cette interface dans le cadre de sa prise en charge pour les références aux objets en mémoire. Cette interface doit être implémentée uniquement si les références sont prises en charge.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Visual Studio appelle [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) pour obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IEnumDebugReferenceInfo2` .

|Méthode|Description|
|------------|-----------------|
|[Next](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Récupère un nombre spécifié de structures de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) dans une séquence d’énumération.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Ignore un nombre spécifié de structures de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) dans la séquence d’énumération.|
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|Réinitialise une séquence d'énumération.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|Obtient le nombre de structures de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) dans un énumérateur.|

## <a name="remarks"></a>Notes
 Une référence est essentiellement un type et une adresse, tandis qu’une propriété est un nom, un type et une adresse. Une référence persiste tant que l’objet référencé existe en mémoire. Pour plus d’informations, consultez [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) .

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
