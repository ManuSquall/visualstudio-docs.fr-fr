---
title: IEnumDebugModules2::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2::Skip
helpviewer_keywords:
- IEnumDebugModules2::Skip
ms.assetid: 61dc42f4-8544-45bb-8da0-fb22cccec7da
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 160dbdedb9dc5f2188036203c2a0b881672dd9ef
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339705"
---
# <a name="ienumdebugmodules2skip"></a>IEnumDebugModules2::Skip
Ignore le nombre spécifié d’éléments.

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
[in] Nombre d’éléments à ignorer.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si `celt` est supérieur au nombre d’éléments restants ; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Si `celt` spécifie une valeur supérieure au nombre d’éléments restants, l’énumération est définie à la fin et `S_FALSE` est retourné.

## <a name="see-also"></a>Voir aussi
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)