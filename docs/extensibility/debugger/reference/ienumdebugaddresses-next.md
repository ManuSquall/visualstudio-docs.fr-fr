---
title: IEnumDebugAddresses::Next Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Next
helpviewer_keywords:
- IEnumDebugAddresses::Next method
ms.assetid: 941e4be7-858d-433a-9259-18d0d017be9e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 88deefddc5b479d7173c4de1c574c4da92631e97
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717640"
---
# <a name="ienumdebugaddressesnext"></a>IEnumDebugAddresses::Next
Cette méthode renvoie la prochaine série d’éléments de l’énumération.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Next(
   ULONG           celt,
   IDebugAddress** rgelt,
   ULONG*          pceltFetched
);
```

```csharp
int Next(
   uint            celt,
   IDebugAddress[] rgelt,
   ref uint        pceltFetched
);
```

## <a name="parameters"></a>Paramètres
`celt`\
[in] Nombre d'éléments à récupérer. Spécifie également la `rgelt` taille maximale du tableau.

`rgelt`\
[dans, dehors] Array d’éléments [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) à remplir.

`pceltFetched`\
[out] Retourne le nombre d’éléments effectivement retournés dans `rgelt`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retours `S_FALSE` si moins que le nombre demandé d’éléments pouvait être retourné; autrement, renvoie un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
