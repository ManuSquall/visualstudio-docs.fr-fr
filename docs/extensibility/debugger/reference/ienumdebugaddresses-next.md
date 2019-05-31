---
title: IEnumDebugAddresses::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Next
helpviewer_keywords:
- IEnumDebugAddresses::Next method
ms.assetid: 941e4be7-858d-433a-9259-18d0d017be9e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 88462448ca05b1e064d39fb0d969491dac8cadda
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330046"
---
# <a name="ienumdebugaddressesnext"></a>IEnumDebugAddresses::Next
Cette méthode retourne l’ensemble suivant d’éléments de l’énumération.

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
[in] Le nombre d’éléments à récupérer. Spécifie également la taille maximale de la `rgelt` tableau.

`rgelt`\
[in, out] Tableau de [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) éléments doit être renseigné.

`pceltFetched`\
[out] Retourne le nombre d’éléments réellement retournés dans `rgelt`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si inférieur au nombre demandé d’éléments peut être retournés ; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)