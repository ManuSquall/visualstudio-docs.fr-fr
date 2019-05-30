---
title: IEnumDebugReferenceInfo2::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2::Next
helpviewer_keywords:
- IEnumDebugReferenceInfo2::Next
ms.assetid: 70b31a57-1701-4757-9e7e-63ec60a71b3c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0860210a2ed80374346268012ae98cf5704b4c7a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322649"
---
# <a name="ienumdebugreferenceinfo2next"></a>IEnumDebugReferenceInfo2::Next
Retourne l’ensemble suivant d’éléments de l’énumération.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Next(
   ULONG                   celt,
   DEBUG_REFERENCE_INFO ** rgelt,
   ULONG*                  pceltFetched
);
```

```csharp
int Next(
   uint                   celt,
   DEBUG_REFERENCE_INFO[] rgelt,
   ref uint               pceltFetched
);
```

## <a name="parameters"></a>Paramètres
`celt`\
[in] Le nombre d’éléments à récupérer. Spécifie également la taille maximale de la `rgelt` tableau.

`rgelt`\
[in, out] Tableau de [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) éléments doit être renseigné.

`pceltFetched`\
[out] Retourne le nombre d’éléments réellement retournés dans `rgelt`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si inférieur au nombre demandé d’éléments peut être retournés ; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)