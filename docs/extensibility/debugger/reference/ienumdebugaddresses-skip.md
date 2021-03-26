---
description: Cette méthode ignore le nombre spécifié d’éléments dans l’énumération Addresses.
title: 'IEnumDebugAddresses :: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Skip
helpviewer_keywords:
- IEnumDebugAddresses::Skip method
ms.assetid: ed9a8e71-30ef-414b-9da5-c9a2a251b84e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 082cba541b1074e75e44384cd8ac9e4879cc29c3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083152"
---
# <a name="ienumdebugaddressesskip"></a>IEnumDebugAddresses::Skip
Cette méthode ignore le nombre spécifié d’éléments.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Skip(
   [in] ULONG celt
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

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si `celt` est supérieur au nombre d’éléments restants ; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Si `celt` spécifie une valeur supérieure au nombre d’éléments restants, l’énumération est définie à la fin et `S_FALSE` est retournée.

## <a name="see-also"></a>Voir aussi
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
