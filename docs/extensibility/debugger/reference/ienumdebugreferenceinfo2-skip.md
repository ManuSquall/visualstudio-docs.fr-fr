---
title: IEnumDebugReferenceInfo2::Skip Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2::Skip
helpviewer_keywords:
- IEnumDebugReferenceInfo2::Skip
ms.assetid: 12f07ed8-92bd-47b5-9113-f73fec5bdde6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2c2247b30d1f300992ef86f80fe44e8ea680fc15
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715285"
---
# <a name="ienumdebugreferenceinfo2skip"></a>IEnumDebugReferenceInfo2::Skip
Ignore le nombre spécifié d'éléments.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Skip(
   ULONG celt
);
```

```csharp
int Skip(
   uint celt
);
```

## <a name="parameters"></a>Paramètres
`celt`\
[in] Nombre d'éléments à ignorer.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. `S_FALSE` Rendements `celt` si c’est supérieur au nombre d’éléments restants; autrement, renvoie un code d’erreur.

## <a name="remarks"></a>Notes
 Si `celt` s’il spécifie une valeur supérieure au nombre d’éléments restants, le recensement est réglé à la fin et `S_FALSE` est retourné.

## <a name="see-also"></a>Voir aussi
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
