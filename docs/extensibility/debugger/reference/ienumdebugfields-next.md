---
title: IEnumDebugFields::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Next
helpviewer_keywords:
- IEnumDebugFields::Next method
ms.assetid: 22c177a2-af81-4234-812b-f9b47be245a2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ee2cc5273b5ec47f99916a308312f6d26c718033
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350424"
---
# <a name="ienumdebugfieldsnext"></a>IEnumDebugFields::Next
Cette méthode retourne l’ensemble suivant d’éléments de l’énumération.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Next(
   ULONG         celt,
   IDebugField** rgelt,
   ULONG*        pceltFetched
);
```

```csharp
int Next(
   uint          celt,
   IDebugField[] rgelt,
   ref uint      pceltFetched
);
```

## <a name="parameters"></a>Paramètres
`celt`\
[in] Le nombre d’éléments à récupérer. Spécifie également la taille maximale de la `rgelt` tableau.

`rgelt`\
[in, out] Tableau de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) éléments doit être renseigné.

`pceltFetched`\
[out] Retourne le nombre d’éléments réellement retournés dans `rgelt`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si inférieur au nombre demandé d’éléments peut être retournés ; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)