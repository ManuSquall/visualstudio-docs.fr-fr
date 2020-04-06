---
title: IEnumDebugPropertyInfo2::Next Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2::Next
helpviewer_keywords:
- IEnumDebugPropertyInfo2::Next
ms.assetid: 4eb8c7c3-aadf-4187-abee-c0620308a3eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d8e714f281835adf7df8d7e96a910ca66f1949b4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715523"
---
# <a name="ienumdebugpropertyinfo2next"></a>IEnumDebugPropertyInfo2::Next
Retourne l'ensemble d'éléments suivants de l'énumération.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Next(
   ULONG                 celt,
   DEBUG_PROPERTY_INFO** rgelt,
   ULONG*                pceltFetched
);
```

```csharp
int Next(
   uint                  celt,
   DEBUG_PROPERTY_INFO[] rgelt,
   ref uint              pceltFetched
);
```

## <a name="parameters"></a>Paramètres
`celt`\
[in] Nombre d'éléments à récupérer. Spécifie également la `rgelt` taille maximale du tableau.

`rgelt`\
[dans, dehors] Array d’éléments [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) à remplir.

`pceltFetched`\
[out] Retourne le nombre d’éléments effectivement retournés dans `rgelt`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retours `S_FALSE` si moins que le nombre demandé d’éléments pouvait être retourné; autrement, renvoie un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
