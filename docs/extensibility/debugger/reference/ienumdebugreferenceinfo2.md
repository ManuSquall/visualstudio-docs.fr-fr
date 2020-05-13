---
title: IEnumDebugReferenceInfo2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6132235a7e4789c7d9efe5bae9d7fd531112dab4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715275"
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
Cette interface énumère les structures [DEBUG_REFERENCE_INFO.](../../../extensibility/debugger/reference/debug-reference-info.md)

## <a name="syntax"></a>Syntaxe

```
IEnumDebugReferenceInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogé (DE) implémente cette interface dans le cadre de son support pour les références aux objets en mémoire. Cette interface ne doit être implémentée que si les références sont prises en charge.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Visual Studio appelle [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) pour obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IEnumDebugReferenceInfo2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[Suivant](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|Récupère un nombre précis de structures [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) dans une séquence de recensement.|
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|Passe un nombre précis de structures [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) dans la séquence de recensement.|
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|Réinitialise une séquence d'énumération.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|Crée un enumérateur qui contient le même état de recensement que l’enumérateur actuel.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|Obtient le nombre de structures [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) dans un enumérateur.|

## <a name="remarks"></a>Notes
 Une référence est essentiellement un type et une adresse, alors qu’une propriété est un nom, un type et une adresse. Une référence persiste tant que l’objet mentionné existe dans la mémoire. Voir [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) pour plus de détails.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
